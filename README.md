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
rabbitmq_version: "3.12.14"
```

The RabbitMQ version to install.

```yaml
rabbitmq_rpm: "rabbitmq-server-{{ rabbitmq_version }}-1.el8.noarch.rpm"
rabbitmq_rpm_url: "https://github.com/rabbitmq/rabbitmq-server/releases/download/v{{ rabbitmq_version }}/{{ rabbitmq_rpm }}"
rabbitmq_rpm_gpg_url: https://www.rabbitmq.com/rabbitmq-release-signing-key.asc
```

(RedHat/CentOS only) Controls the .rpm to install.

```yaml
rabbitmq_apt_repository: "https://deb1.rabbitmq.com/rabbitmq-server/{{ ansible_facts.distribution | lower }}/{{ ansible_facts.distribution_release }}"
erlang_apt_repository: "https://deb1.rabbitmq.com/rabbitmq-erlang/{{ ansible_facts.distribution | lower }}/{{ ansible_facts.distribution_release }}"
rabbitmq_apt_keyring_path: "/usr/share/keyrings/com.rabbitmq.team.gpg"
rabbitmq_apt_key_fingerprint: "0A9AF2115F4687BD29803A206B73A36E6026DFCA"
```

(Debian/Ubuntu only) Controls the repository configuration for the installation.
The role uses RabbitMQ's `deb1` mirror plus the Team RabbitMQ signing key by
default. If `rabbitmq_apt_keyring_path` is unset, the role falls back to the
legacy `rabbitmq_apt_gpg_url` / `erlang_apt_gpg_url` locations instead.

## Dependencies

None.

## Example Playbook

```yaml
- hosts: rabbitmq
  roles:
    - name: geerlingguy.repo-epel
      when: ansible_facts.os_family == 'RedHat'
    - geerlingguy.rabbitmq
```

## License

MIT / BSD

## Author Information

This role was created in 2017 by [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).
