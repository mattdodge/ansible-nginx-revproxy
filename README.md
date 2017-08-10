ansible-nginx-revproxy
=========
[![Build Status](https://img.shields.io/travis/hispanico/ansible-nginx-revproxy.svg?style=flat-square)](https://travis-ci.org/hispanico/ansible-nginx-revproxy)
[![Galaxy](https://img.shields.io/badge/galaxy-hispanico.nginx-revproxy-blue.svg?style=flat-square)](https://galaxy.ansible.com/hispanico/nginx-revproxy/)

Install and configures Nginx as reverse proxy for multiple website.

Requirements
------------

This role requires Ansible 1.9 or higher.

Role Variables
--------------

Default values:

```yaml
nginx_revproxy_sites:                                                        # List of sites
  example.com:                                                # Domain name
    domains:                                                  # List of server_name aliases
      - example.com
      - www.example.com
    upstreams:                                                # List of Upstreams
      - { backend_address: 192.168.0.100, backend_port: 80 }
      - { backend_address: 192.168.0.101, backend_port: 8080 }
    letsencrypt: false                                        # Set to True after the first run if you are using hispanico.letsencrypt role
```

Dependencies
------------

None.

Example Playbook
----------------

```yaml
  - hosts: all
    roles:
      - ansible-nginx-revproxy
    vars:
      nginx_revproxy_sites:
        example.com:
          domains:
            - example.com
            - www.example.com
          upstreams:
            - { backend_address: 192.168.0.100, backend_port: 80 }
            - { backend_address: 192.168.0.101, backend_port: 80 }
          letsencrypt: false
```

License
-------

Licensed under the GPLv3 License. See the LICENSE file for details.

Author Information
------------------

Hispanico