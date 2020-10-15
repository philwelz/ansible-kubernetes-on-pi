**Table of Contents** 

- [Docker](#docker)
  - [Requirements](#requirements)
  - [Role Variables](#role-variables)
  - [Example Playbook](#example-playbook)
  - [Configuration](#configuration)
  - [License](#license)

# docker

## Requirements

You probably want to run the role with `become: true`

## Role Variables

[defaults/main.yml](https://github.com/philwelz/ansible-playbooks/blob/master/roles/docker/defaults/main.yaml)

```yaml
---
docker_apt_key: "https://download.docker.com/linux/ubuntu/gpg"
docker_repo: "deb [arch=arm64] https://download.docker.com/linux/ubuntu focal stable"
docker_packages: 
  - docker-ce=5:19.03.13~3-0~ubuntu-focal
  - docker-ce-cli=5:19.03.13~3-0~ubuntu-focal
  - containerd.io=1.3.7-1
docker_service_state: started
docker_service_enabled: true
```

## Example Playbook

```yaml
---
- name: PI
  hosts: ...your hosts...
  roles:
    - role: docker
      become: true
```

## Configuration

```yaml
docker_packages: 
  - docker-ce=5:19.03.13~3-0~ubuntu-focal
  - docker-ce-cli=5:19.03.13~3-0~ubuntu-focal
  - containerd.io=1.3.7-1
```

## License

MIT