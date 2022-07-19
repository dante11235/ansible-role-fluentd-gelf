Ansible Role: ansible_role_fluentd_gelf
=========

Ansible galaxy role to install fluentd with gelf support

Requirements
------------

No extra requirements.

Role Variables
--------------

```
graylog_server: 192.168.10.10
graylog_gelf_port: 12201
fluentd_conf_sources: |
  <source>
    @type syslog
    tag graylog2
  </source>
fluentd_conf_matches: |
  <match graylog2.**>
    @type gelf
    host {{ graylog_server }}
    port {{ graylog_gelf_port }}
    <buffer>
      flush_interval 5s
    </buffer>
  </match>

```
Dependencies
------------

No dependencies

Example Playbook
----------------
```
- hosts: servers
  become: true

  roles:
    - role: dante11235.fluentd-gelf
      graylog_server: 192.168.10.10
      graylog_gelf_port: 12201
      fluentd_conf_sources: |
        <source>
          @type syslog
          tag graylog2
        </source>
      fluentd_conf_matches: |
        <match graylog2.**>
          @type gelf
          host {{ graylog_server }}
          port {{ graylog_gelf_port }}
          <buffer>
            flush_interval 5s
          </buffer>
        </match>
```
License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
