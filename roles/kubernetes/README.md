**Table of Contents** 

- [pi-fancontrol](#pi-fancontrol)
  - [Requirements](#requirements)
  - [Example Playbook](#example-playbook)
  - [Configuration](#configuration)
  - [License](#license)

# Kubernetes

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
    - role: kubernetes/node
      become: true
      when:  kubernetes_role == 'node'
```

## Configuration

- [common](https://github.com/philwelz/ansible-playbooks/tree/master/roles/kubernetes/common)
- [master](https://github.com/philwelz/ansible-playbooks/tree/master/roles/kubernetes/master)
- [node](https://github.com/philwelz/ansible-playbooks/tree/master/roles/kubernetes/node)


## License

MIT