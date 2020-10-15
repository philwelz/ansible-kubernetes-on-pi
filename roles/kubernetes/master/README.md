**Table of Contents** 

- [kubernetes-common](#kubernetes-common)
  - [Requirements](#requirements)
  - [Role Variables](#role-variables)
  - [Example Playbook](#example-playbook)
  - [Configuration](#configuration)
  - [License](#license)

# kubernetes-master

## Requirements

You probably want to run the role with `become: true`

## Role Variables

[defaults/main.yml](https://github.com/philwelz/ansible-playbooks/blob/master/roles/kubernetes/master/defaults/main.yaml)

```yaml
---
kubernetes_version: '1.19.2'
kubernetes_service_cidr: "10.96.0.0/12"
kubernetes_kubeadm_config: "/etc/kubernetes/admin.conf"
kubernetes_kubeadm_ca: "/etc/kubernetes/pki/ca.key"
kubernetes_kubelet_extra_args: ""
kubernetes_kubeadm_init_extra_opts: ""
kubernetes_join_command_extra_opts: ""
kubernetes_version_kubeadm: 'stable-{{ kubernetes_version }}'
kubernetes_ignore_preflight_errors: 'all'
kubernetes_pod_network:
  # Calico CNI.
  cni: 'calico'
  cidr: '10.10.0.0/16'
# Variables for Calico Installation
#calico_repo: "https://docs.projectcalico.org/v3.4/getting-started/kubernetes/installation/hosted/calico.yaml"
kubernetes_calico_manifest_file: "https://docs.projectcalico.org/manifests/calico.yaml"
```

## Example Playbook

```yaml
---
- name: PI
  hosts: ...your hosts...
  roles:
    - role: kubernetes/master
      become: true
      when:  kubernetes_role == 'master'
```

## Configuration

## License

MIT