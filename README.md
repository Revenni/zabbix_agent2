revenni.zabbix_agent2
=========

Ansible role providing the installation and configuration of Zabbix agent. Compatible with zabbix >=4.4, 5.0, and 5.2.

[![Platforms](http://img.shields.io/badge/platforms-ubuntu-lightgrey.svg?style=flat)](#)
[![Platforms](http://img.shields.io/badge/platforms-debian-lightgrey.svg?style=flat)](#)
[![Licence](https://img.shields.io/badge/Licence-MIT-blue.svg)](https://tldrlegal.com/license/mit-license)

Requirements
------------

* Accurate inventory_hostname

Role Variables
--------------

### Generic variables (declared in defaults/main.yml + overridden in vars/main.yml)
* ```zabbix_version``` (5.0) - zabbix version.  must be >= 4.4 for agent2.
* ```zabbix_agent_pid_file``` (/var/run/zabbix/zabbix_agent2.pid) - path to pid file
* ```zabbix_agent_log_file``` (/var/log/zabbix/zabbix_agent2.log) - path to zabbix agent log
* ```zabbix_agent_config_file``` (/etc/zabbix/zabbix_agent2.conf) - config file for zabbix agent
* ```zabbix_agent_control_socket_path``` (/tmp/agent.sock) - path to control socket
* ```zabbix_agent_include_path``` (/etc/zabbix/zabbix_agent2.d/*.conf) - path to userparameter files
* ```zabbix_agent_psk_file``` (/etc/zabbix/zabbix_agent2.psk) - pre shared key file
* ```zabbix_agent_psk_hash``` (kmWCW6jtSSFK7XRuMJct2fVINNL1QTYt) - pre shared keys are an md5 of inventory_hostname + hash specified here.  Please change this by running ```pwgen -s 32 1```
* ```zabbix_agent_log_size``` (0) - size in MB to rotate log.  0 = use logrotate
* ```zabbix_agent_server_ip``` (127.0.0.1) - ip address of zabbix server
* ```zabbix_agent_server_active_ip``` (127.0.0.1) - ip of zabbix server providing active checks
* ```zabbix_agent_timeout``` (3) - amount of time to spend on processing
* ```zabbix_agent_allow_remote_commands``` (false) - allow zabbix-server to invoke commands on this agent when set to `true`.

Dependencies
------------

* None

Example Playbook
----------------

    - hosts: all
      become: true
      roles:
         - { role: revenni.zabbix_agent2, tags: zabbix_agent2 }

License
-------

MIT

Author Information
------------------
* [Vince Hillier](https://revenni.com) | [@email](mailto:vince@revenni.com) | [twitter](https://twitter.com/vincedotca)
