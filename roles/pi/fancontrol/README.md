**Table of Contents** 

- [pi-fancontrol](#pi-fancontrol)
  - [Requirements](#requirements)
  - [Role Variables](#role-variables)
  - [Example Playbook](#example-playbook)
  - [Configuration](#configuration)
  - [License](#license)

# pi-fancontrol

## Requirements

You probably want to run the role with `become: true`

## Role Variables

[defaults/main.yml](https://github.com/philwelz/ansible-playbooks/blob/master/roles/pi-fancontrol/defaults/main.yaml)

```yaml
---
fancontrol_enabled: true
fan_config_file: /etc/udev/rules.d/50-rpi-fan.rules
fan_config_template: fancontrol.jinja2
```

## Example Playbook

```yaml
---
- name: PI
  hosts: ...your hosts...
  roles:
    - role: pi-fancontrol
      become: true
      when: ansible_os_family == 'Debian' 
```

## Configuration

* `/boot/firmware/usercfg.txt`

```bash
# Place "config.txt" changes (dtparam, dtoverlay, disable_overscan, etc.) in
# this file. Please refer to the README file for a description of the various
# configuration files on the boot partition.
dtoverlay=rpi-poe
dtparam=poe_fan_temp0=61000,poe_fan_temp0_hyst=2000
dtparam=poe_fan_temp1=70000,poe_fan_temp1_hyst=5000
dtparam=poe_fan_temp2=75000,poe_fan_temp2_hyst=3000
dtparam=poe_fan_temp3=81000,poe_fan_temp3_hyst=5000
```
## License

MIT