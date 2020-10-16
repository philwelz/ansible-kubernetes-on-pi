**Table of Contents** 

- [pi-system](#pi-system)
  - [Requirements](#requirements)
  - [Role Variables](#role-variables)
  - [Example Playbook](#example-playbook)
  - [License](#license)

# pi-system

## Requirements

You probably want to run the role with `become: true`

## Role Variables

[defaults/main.yml](https://github.com/philwelz/ansible-playbooks/blob/master/roles/pi-system/defaults/main.yaml)

```yaml
---
system_packages:
  - apt-transport-https
  - ca-certificates
  - curl
  - gnupg-agent
  - software-properties-common
  - lm-sensors
```

## Example Playbook

```yaml
---
- name: PI
  hosts: ...your hosts...
  roles:
    - role: pi-system
      become: true
      when: ansible_os_family == 'Debian' 
```

## License

MIT