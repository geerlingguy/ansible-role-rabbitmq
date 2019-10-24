# Ansible Role: RabbitMQ

[![Build Status](https://travis-ci.org/geerlingguy/ansible-role-rabbitmq.svg?branch=master)](https://travis-ci.org/geerlingguy/ansible-role-rabbitmq)

Installs RabbitMQ on Linux.

## Requirements

(Red Hat / CentOS only) Requires the EPEL repository, which can be installed with the `geerlingguy.repo-epel` role.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    rabbitmq_daemon: rabbitmq-server
    rabbitmq_state: started
    rabbitmq_enabled: true

Controls the RabbitMQ daemon's state and whether it starts at boot.

    rabbitmq_version: "3.8.0"

The RabbitMQ version to install.

    rabbitmq_basename: "rabbitmq-server"

(RedHat/CentOS only) The RabbitMQ package basename.
    
    erlang_yum_repository_url: "https://packagecloud.io/install/repositories/rabbitmq/erlang/config_file.repo?os={{ansible_distribution | lower}}&dist={{ ansible_distribution_major_version }}&source=script"
    rabbitmq_yum_repository_url: "https://packagecloud.io/install/repositories/rabbitmq/rabbitmq-server/config_file.repo?os={{ansible_distribution | lower}}&dist={{ansible_distribution_major_version | lower}}&source=script"
    erlang_yum_repository_path: "/etc/yum.repos.d/rabbitmq_erlang.repo"
    rabbitmq_yum_repository_path: "/etc/yum.repos.d/rabbitmq_rabbitmq-server.repo"

(RedHat/CentOS only) Controls the Package Cloud repositories for RabbitMQ and Erlang latest versions

    rabbitmq_deb: "rabbitmq-server_{{ rabbitmq_version }}-1_all.deb"
    rabbitmq_deb_url: "https://packagecloud.io/rabbitmq/rabbitmq-server/packages/{{ ansible_distribution | lower }}/{{ ansible_distribution_release }}/{{ rabbitmq_deb }}/download"

(Debian/Ubuntu only) Controls the .deb to install.

## Dependencies

None.

## Example Playbook

    - hosts: rabbitmq
      roles:
        - name: geerlingguy.repo-epel
          when: ansible_os_family == 'RedHat'
        - geerlingguy.rabbitmq

## License

MIT / BSD

## Author Information

This role was created in 2017 by [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).
