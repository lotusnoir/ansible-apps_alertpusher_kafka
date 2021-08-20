# Ansible Role: ansible-apps_alertpusher_kafka

## Description

[![Build Status](https://travis-ci.com/lotusnoir/ansible-apps_alertpusher_kafka.svg?branch=master?style=flat)](https://travis-ci.com/lotusnoir/ansible-apps_alertpusher_kafka)
[![License](https://img.shields.io/badge/license-Apache--2.0-brightgreen?style=flat)](https://opensource.org/licenses/Apache-2.0)
[![Ansible Role](https://img.shields.io/badge/galaxy-apps_alertpusher_kafka-purple?style=flat)](https://galaxy.ansible.com/lotusnoir/apps_alertpusher_kafka)
![GitHub repo size](https://img.shields.io/github/repo-size/lotusnoir/ansible-apps_alertpusher_kafka?color=orange&style=flat)
![Ansible Quality Score](https://img.shields.io/ansible/quality/52300)
[![downloads](https://img.shields.io/ansible/role/d/52300)](https://galaxy.ansible.com/lotusnoir/apps_alertpusher_kafka)
[![Version](https://img.shields.io/github/release/lotusnoir/ansible-apps_alertpusher_kafka.svg)](https://github.com/lotusnoir/ansible-apps_alertpusher_kafka/releases/)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=lotusnoir_ansible-apps_alertpusher_kafka&metric=alert_status)](https://sonarcloud.io/dashboard?id=lotusnoir_ansible-apps_alertpusher_kafka)
[![Maintainability Rating](https://sonarcloud.io/api/project_badges/measure?project=lotusnoir_ansible-apps_alertpusher_kafka&metric=sqale_rating)](https://sonarcloud.io/dashboard?id=lotusnoir_ansible-apps_alertpusher_kafka)
[![Reliability Rating](https://sonarcloud.io/api/project_badges/measure?project=lotusnoir_ansible-apps_alertpusher_kafka&metric=reliability_rating)](https://sonarcloud.io/dashboard?id=lotusnoir_ansible-apps_alertpusher_kafka)
[![Security Rating](https://sonarcloud.io/api/project_badges/measure?project=lotusnoir_ansible-apps_alertpusher_kafka&metric=security_rating)](https://sonarcloud.io/dashboard?id=lotusnoir_ansible-apps_alertpusher_kafka)

Deploy [alertpusher_kafka](https://github.com/lotusnoir/alertmanager-apps_alertpusher_kafka) to send prometheus alerts to kafka topic.

## Role variables

| Name                                  | Default Value          | Description                        |
| ------------------------------------- | ---------------------- | -----------------------------------|
| `alertpusher_kafka_install_dir`       | /usr/local/bin         | directory to install binary |
| `alertpusher_kafka_force_install`     | false                  | force install variable |
| `alertpusher_kafka_src_dir`           | /tmp/alertpusher_kafka | temp dir to build sources |
| `alertpusher_kafka_debug`             |                        | |
| `alertpusher_kafka_sensu_client_port` |                        | |
| `alertpusher_kafka_sensu_api_port`    |                        | |
| `alertpusher_kafka_targets`           |                        | |

## Examples

	---
	- hosts: apps_alertpusher_kafka
	  become: yes
	  become_method: sudo
	  gather_facts: yes
	  roles:
	    - role: ansible-apps_alertpusher_kafka
      vars:
        alertpusher_kafka_targets:
          - name: test1
            port: 8088
            host: kafka1.example.net,kafka2.example.net
            topic: alert_noc
            partition: 2 # 0 is not set
            log_dir: /var/log/alertpusher_kafka/ # stderr if not set
            skip_resolved: true # false when not set
	  environment: 
	    http_proxy: "{{ http_proxy }}"
	    https_proxy: "{{ https_proxy }}"
	    no_proxy: "{{ no_proxy }}

## License

This project is licensed under Apache License. See [LICENSE](/LICENSE) for more details.
