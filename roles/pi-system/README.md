**Table of Contents** 

- [pi-system](#pi-system)
  - [Requirements](#requirements)
  - [Role Variables](#role-variables)
  - [Example Playbook](#example-playbook)
  - [Configuration](#configuration)
  - [License](#license)

# pi-system

## Requirements

You probably want to run the role with `become: true`

## Role Variables

[defaults/main.yml](defaults/main.yml)

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

## Configuration

* `/etc/udev/rules.d/50-rpi-fan.rules`

```bash
SUBSYSTEM=="thermal"
KERNEL=="thermal_zone0"

# If the temp hits 81C, highest RPM
ATTR{trip_point_0_temp}="82000"
ATTR{trip_point_0_hyst}="3000"
#
# If the temp hits 80C, higher RPM
ATTR{trip_point_1_temp}="81000"
ATTR{trip_point_1_hyst}="2000"
#
# If the temp hits 70C, higher RPM
ATTR{trip_point_2_temp}="71000"
ATTR{trip_point_2_hyst}="3000"
#
# If the temp hits 60C, turn on the fan
ATTR{trip_point_3_temp}="61000"
ATTR{trip_point_3_hyst}="5000"
#
# Fan is off otherwise
```
## License

MIT