# Ansible Role: RabbitMQ

[![Build Status](https://travis-ci.org/geerlingguy/ansible-role-rabbitmq.svg?branch=master)](https://travis-ci.org/geerlingguy/ansible-role-rabbitmq)

Installs RabbitMQ on Linux.

## Requirements

(Red Hat / CentOS only) Requires the EPEL repository, which can be installed with the `geerlingguy.repo-epel` role.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

### Default Values
    rabbitmq_daemon: rabbitmq-server
    rabbitmq_state: started
    rabbitmq_enabled: yes

    rabbitmq_version: "3.6.11"

    rabbitmq_baseurl: https://dl.bintray.com/rabbitmq/all/rabbitmq-server
    rabbitmq_rpm: "rabbitmq-server-{{ rabbitmq_version }}-1.el{{ ansible_distribution_major_version }}.noarch.rpm"
    
    rabbitmq_deb: "rabbitmq-server_{{ rabbitmq_version }}-1_all.deb"

There are currently no available variables outside of the default values.

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
