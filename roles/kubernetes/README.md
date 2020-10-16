**Table of Contents** 

- [Kubernetes](#kubernetes)
  - [Requirements](#requirements)
  - [Example Playbook](#example-playbook)
  - [Configuration](#configuration)
  - [License](#license)

# Kubernetes

Role for configuring Kubernetes.

## Requirements

You probably want to run the role with `become: true`

## Example Playbook

```yaml
---
- name: PI
  hosts: ...your hosts...
  roles:
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

## Configuration

- Kubernetes Container Network Interface
  - [cni](https://github.com/philwelz/ansible-playbooks/tree/master/roles/kubernetes/cni)
- Common Kubernetes Package including kubeadm, kubelet & kubectl
  - [common](https://github.com/philwelz/ansible-playbooks/tree/master/roles/kubernetes/common)
- Init Cluster
  - [master](https://github.com/philwelz/ansible-playbooks/tree/master/roles/kubernetes/master)
- Join Nodes to the Cluster
  - [node](https://github.com/philwelz/ansible-playbooks/tree/master/roles/kubernetes/node)

## License

MIT