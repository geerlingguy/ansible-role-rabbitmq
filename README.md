# Ansible Role: RabbitMQ

[![CI](https://github.com/geerlingguy/ansible-role-rabbitmq/workflows/CI/badge.svg?event=push)](https://github.com/geerlingguy/ansible-role-rabbitmq/actions?query=workflow%3ACI)

Installs RabbitMQ on Linux and open ports in firewall (Centos/Rocky/RHEL only)

## Requirements

(Red Hat / CentOS only) Requires the EPEL repository, which can be installed with the `geerlingguy.repo-epel` role.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    rabbitmq_daemon: rabbitmq-server
    rabbitmq_state: started
    rabbitmq_enabled: true

Controls the RabbitMQ daemon's state and whether it starts at boot.

    rabbitmq_version: "3.9.13"

The RabbitMQ version to install.

    rabbitmq_rpm: "rabbitmq-server-{{ rabbitmq_version }}-1.el{{ ansible_distribution_major_version }}.noarch.rpm"
    rabbitmq_rpm_url: "https://packagecloud.io/rabbitmq/rabbitmq-server/packages/el/{{ ansible_distribution_major_version }}/{{ rabbitmq_rpm }}/download"

(RedHat/CentOS only) Controls the .rpm to install.

    rabbitmq_deb: "rabbitmq-server_{{ rabbitmq_version }}-1_all.deb"
    rabbitmq_deb_url: "https://packagecloud.io/rabbitmq/rabbitmq-server/packages/{{ ansible_distribution | lower }}/{{ ansible_distribution_release }}/{{ rabbitmq_deb }}/download"

(Debian/Ubuntu only) Controls the .deb to install.

Open firewall ports:
    rabbit_firewall: true

User with admin rights with password abc

    rabbit_admin: "rabbit_admin"
    rabbit_admin_password: "abc"

Enable cluster setup:
    rabbit_primary_node: ansible_nodename of primary node
    
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
