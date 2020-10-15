**Table of Contents** 

- [Ansible-kubernetes-on-pi](#ansible-kubernetes-on-pi)
  - [Requirements](#requirements)
  - [Roles](#roles)
  - [Inventory](#inventory)
  - [Configuration](#configuration)
  - [License](#license)

# ansible-kubernetes-on-pi

## Requirements

**Work in Progress** 


## Playbooks

- [kubernetes](https://github.com/philwelz/ansible-playbooks/tree/master/kubernetes.yaml)

## Roles:

- [docker](https://github.com/philwelz/ansible-playbooks/tree/master/roles/docker)
- [kubernetes](https://github.com/philwelz/ansible-playbooks/tree/master/roles/kubernetes)
- [pi-fancontrol](https://github.com/philwelz/ansible-playbooks/tree/master/roles/pi-fancontrol)
- [pi-system](https://github.com/philwelz/ansible-playbooks/tree/master/roles/pi-system)


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
          kbernetes_role: node
```

## Usage

`ansible-playbook kubernetes.yaml -i inventory.yaml -u USER -k`

## License

MIT