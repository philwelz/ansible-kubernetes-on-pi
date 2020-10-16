**Table of Contents** 

- [kubernetes-cni](#kubernetes-cni)
  - [Requirements](#requirements)
  - [Role Variables](#role-variables)
  - [Example Playbook](#example-playbook)
  - [Configuration](#configuration)
  - [License](#license)

# kubernetes-cni

Sub-Role for installing kubeadm, kubelet & kubectl.

## Requirements

You probably want to run the role with `become: true`

## Role Variables

[defaults/main.yml](https://github.com/philwelz/ansible-kubernetes-on-pi/blob/master/roles/kubernetes/cni/defaults/main.yaml)

```yaml
kubernetes_pod_network:
  # Calico CNI.
  cni: 'calico'
  # Calico Flannel.
  #cni: 'flannel'
  # Calico Weave.
  #cni: 'weave'

# Variables for Calico Installation
#calico_repo: "https://docs.projectcalico.org/v3.4/getting-started/kubernetes/installation/hosted/calico.yaml"
calico_manifest_file: "https://docs.projectcalico.org/manifests/calico.yaml"
```

## Example Playbook

```yaml
---
- name: PI
  hosts: ...your hosts...
  roles:
    - role: kubernetes/cni
      become: true
      when:  kubernetes_role == 'master'
```

## Configuration

## License

MIT