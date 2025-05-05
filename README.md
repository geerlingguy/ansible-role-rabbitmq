# Ansible Role: RabbitMQ

[![CI](https://github.com/geerlingguy/ansible-role-rabbitmq/actions/workflows/ci.yml/badge.svg)](https://github.com/geerlingguy/ansible-role-rabbitmq/actions/workflows/ci.yml)

Installs RabbitMQ on Linux.

## Requirements

(Red Hat / CentOS only) Requires the EPEL repository, which can be installed with the `geerlingguy.repo-epel` role.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
rabbitmq_daemon: rabbitmq-server
rabbitmq_state: started
rabbitmq_enabled: true
```

Controls the RabbitMQ daemon's state and whether it starts at boot.

```yaml
rabbitmq_version: "3.9.13"
```

The RabbitMQ version to install.

```yaml
rabbitmq_rpm: "rabbitmq-server-{{ rabbitmq_version }}-1.el8.noarch.rpm"
rabbitmq_rpm_url: "https://github.com/rabbitmq/rabbitmq-server/releases/download/v{{ rabbitmq_version }}/{{ rabbitmq_rpm }}"
rabbitmq_rpm_gpg_url: https://www.rabbitmq.com/rabbitmq-release-signing-key.asc
```

(RedHat/CentOS only) Controls the .rpm to install.

```yaml
rabbitmq_apt_repository: "deb [signed-by=/etc/apt/trusted.gpg.d/rabbitmq-9F4587F226208342.gpg] https://ppa1.novemberain.com/rabbitmq/rabbitmq-server/deb/{{ ansible_distribution | lower }} {{ ansible_distribution_release }} main"
rabbitmq_apt_gpg_url: "https://ppa.novemberain.com/gpg.9F4587F226208342.key"

erlang_apt_repository: "deb [signed-by=/etc/apt/trusted.gpg.d/erlang-E495BB49CC4BBE5B.gpg] https://ppa2.novemberain.com/rabbitmq/rabbitmq-erlang/deb/{{ ansible_distribution | lower }} {{ ansible_distribution_release }} main"
erlang_apt_gpg_url: "https://ppa.novemberain.com/gpg.E495BB49CC4BBE5B.key"
```

(Debian/Ubuntu only) Controls the repository configuration for the installation

## Dependencies

None.

## Example Playbook

```yaml
- hosts: rabbitmq
  roles:
    - name: geerlingguy.repo-epel
      when: ansible_os_family == 'RedHat'
    - geerlingguy.rabbitmq
```

## License

MIT / BSD

## Author Information

This role was created in 2017 by [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).
