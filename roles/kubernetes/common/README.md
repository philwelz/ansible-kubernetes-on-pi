**Table of Contents** 

- [kubernetes-common](#kubernetes-common)
  - [Requirements](#requirements)
  - [Role Variables](#role-variables)
  - [Example Playbook](#example-playbook)
  - [Configuration](#configuration)
  - [License](#license)

# kubernetes-common

Sub-Role for installing kubeadm, kubelet & kubectl.

## Requirements

You probably want to run the role with `become: true`

## Role Variables

[defaults/main.yml](https://github.com/philwelz/ansible-kubernetes-on-pi/blob/master/roles/kubernetes/common/defaults/main.yaml)

```yaml
---
kubernetes_apt_key: "https://packages.cloud.google.com/apt/doc/apt-key.gpg"
kubernetes_apt_repository: "deb https://apt.kubernetes.io/ kubernetes-xenial main"
kubernetes_packages:
  - kubelet=1.19.2-00
  - kubectl=1.19.2-00
  - kubeadm=1.19.2-00
```

## Example Playbook

```yaml
---
- name: PI
  hosts: ...your hosts...
  roles:
    - role: kubernetes/common
      become: true
```

## Configuration

## License

MIT