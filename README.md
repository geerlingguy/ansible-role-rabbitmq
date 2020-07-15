# Ansible Role: RabbitMQ

[![Build Status](https://travis-ci.com/davidalger/ansible-role-rabbitmq.svg?branch=master)](https://travis-ci.com/davidalger/ansible-role-rabbitmq)

Installs RabbitMQ on Linux.

## Requirements

No external dependencies.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    rabbitmq_daemon: rabbitmq-server
    rabbitmq_state: started
    rabbitmq_enabled: true

Controls the RabbitMQ daemon's state and whether it starts at boot.

    rabbitmq_version: "3.8.5"

The RabbitMQ version to install.

    erlang_version: "23.0.2"

The Erlang version to install.

    rabbitmq_rpm: "rabbitmq-server-{{ rabbitmq_version }}-1.el{{ ansible_distribution_major_version }}.noarch.rpm"
    rabbitmq_rpm_url: "https://packagecloud.io/rabbitmq/rabbitmq-server/packages/el/{{ ansible_distribution_major_version }}/{{ rabbitmq_rpm }}/download"

    erlang_rpm: "erlang-{{ erlang_version }}-1.el{{ ansible_distribution_major_version }}.x86_64.rpm"
    erlang_rpm_url: "https://packagecloud.io/rabbitmq/erlang/packages/el/{{ ansible_distribution_major_version }}/{{ erlang_rpm }}/download"

(RedHat/CentOS only) Controls the .rpm to install.

    rabbitmq_deb: "rabbitmq-server_{{ rabbitmq_version }}-1_all.deb"
    rabbitmq_deb_url: "https://packagecloud.io/rabbitmq/rabbitmq-server/packages/{{ ansible_distribution | lower }}/{{ ansible_distribution_release }}/{{ rabbitmq_deb }}/download"

    erlang_deb: "erlang-{{ item }}_{{ erlang_version }}-1_amd64.deb"
    erlang_deb_url: "https://bintray.com/rabbitmq-erlang/debian/download_file?file_path=pool%2Ferlang%2F{{ erlang_version }}-1%2F{{ ansible_distribution | lower }}%2F{{ ansible_distribution_release }}%2Ferlang-{{ item }}_{{ erlang_version }}-1_amd64.deb"

(Debian/Ubuntu only) Controls the .deb to install.

## Dependencies

None.

## Example Playbook

    - hosts: rabbitmq
      roles:
        - davidalger.rabbitmq

## License

MIT / BSD

## Author Information

This role was created in 2017 by [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).
