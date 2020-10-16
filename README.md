![Ansible Lint](https://github.com/philwelz/ansible-kubernetes-on-pi/workflows/Ansible%20Lint/badge.svg)

**Table of Contents** 

- [Ansible-kubernetes-on-pi](#ansible-kubernetes-on-pi)
  - [Requirements](#requirements)
  - [Installed](#installed)
  - [Roles](#roles)
  - [Inventory](#inventory)
  - [Configuration](#configuration)
  - [License](#license)

# ansible-kubernetes-on-pi

## Requirements

- SSH setup on the PIs
- static IPs configured
- `group_enable=cpuset cgroup_memory=1 cgroup_enable=memory` added to `/boot/firmware/cmdline.txt`

## Installed

The following packages will be installed with this playbook.

- Common Packages
  - apt-transport-https
  - ca-certificates
  - curl
  - gnupg-agent
  - software-properties-common
  - lm-sensors
- Docker
  - docker-ce 19.03.13-3
  - docker-ce-cli 19.03.13-3
  - containerd 1.3.7-1
- Kubernetes
  - kubelet 1.19.2
  - kubeadm 1.19.2
  - kubectl 1.19.2
- Calico 3.16.3

## Playbooks

- [kubernetes](https://github.com/philwelz/ansible-playbooks/tree/master/kubernetes.yaml)

```yaml
---
- name: Kubernetes
  hosts: all
  roles:
    - role: pi/packages
      become: true
      when: hardware == 'pi'
    - role: pi/packages
      become: true
      when: hardware == 'pi'
    - role: docker
      become: true
    - role: kubernetes/common
      become: true
    - role: kubernetes/master
      become: true
      when:  kubernetes_role == 'master'
    - role: kubernetes/cni
      become: true
      when:  kubernetes_role == 'master'
    - role: kubernetes/node
      become: true
      when:  kubernetes_role == 'node'
```

## Roles:

- [docker](https://github.com/philwelz/ansible-playbooks/tree/master/roles/docker)
- [kubernetes](https://github.com/philwelz/ansible-playbooks/tree/master/roles/kubernetes)
- [pi](https://github.com/philwelz/ansible-playbooks/tree/master/roles/pi)

## Inventory

```yaml
---
all:
  hosts:
  children:
    k8smaster:
      hosts:
        1.2.3.4:
          kubernetes_role: master
          hardware: pi
    k8snodes:
      hosts:
        4.3.2.1:
          kubernetes_role: node
          hardware: pi
        5.6.7.8:
          kubernetes_role: node
          hardware: pi
```

## Usage

`ansible-playbook kubernetes.yaml -i inventory.yaml -u USER -k`

## License

MIT