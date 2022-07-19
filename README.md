Role Name
=========

Ansible galaxy role to install fluentd with gelf support

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

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
