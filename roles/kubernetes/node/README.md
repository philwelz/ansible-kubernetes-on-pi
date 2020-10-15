**Table of Contents** 

- [kubernetes-node](#kubernetes-node)
  - [Requirements](#requirements)
  - [Role Variables](#role-variables)
  - [Example Playbook](#example-playbook)
  - [Configuration](#configuration)
  - [License](#license)

# kubernetes-node

## Requirements

You probably want to run the role with `become: true`

## Role Variables

## Example Playbook

```yaml
---
- name: PI
  hosts: ...your hosts...
  roles:
    - role: kubernetes/node
      become: true
      when:  kubernetes_role == 'node'
```

## Configuration

## License

MIT