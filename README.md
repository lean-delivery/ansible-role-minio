minio role
=========
[![License](https://img.shields.io/badge/license-Apache-green.svg?style=flat)](https://raw.githubusercontent.com/lean-delivery/ansible-role-minio/master/LICENSE)
[![Build Status](https://travis-ci.org/lean-delivery/ansible-role-minio.svg?branch=master)](https://travis-ci.org/lean-delivery/ansible-role-minio)
[![Build Status](https://gitlab.com/lean-delivery/ansible-role-minio/badges/master/build.svg)](https://gitlab.com/lean-delivery/ansible-role-minio/pipelines)
[![Galaxy](https://img.shields.io/badge/galaxy-lean__delivery.minio-blue.svg)](https://galaxy.ansible.com/lean_delivery/minio)
![Ansible](https://img.shields.io/ansible/role/d/39136.svg)
![Ansible](https://img.shields.io/badge/dynamic/json.svg?label=min_ansible_version&url=https%3A%2F%2Fgalaxy.ansible.com%2Fapi%2Fv1%2Froles%2F39136%2F&query=$.min_ansible_version)

This role:
  - installs Minio server on Ubuntu, Centos7, RHEL7
  - enables Minio service to systemd

Requirements
------------

- **Supported OS**:
   - CentOS
     - 7
   - RHEL
     - 7
   - Ubuntu

Role Variables
--------------

  - `minio_home` - Path where Minio will be placed
     default: `/opt/minio`
  - `minio_user` - User for Minio's action   
     default: `minio`
  - `minio_group` - Minio user's group  
     default: `minio`
  - `minio_package_source` - Source from which should be downloded binary file   
     default: `https://dl.minio.io/server/minio/release/linux-amd64/minio`
  - `minino_data_path` - Minio data folder   
     default: `'{{ minio_home }}/data'`
  - `minio_http_port` - Port for listening connections   
     default: `9000`
  - `minio_access_key` - Access key for log in   
  - `minio_secret_key` - Secret key for log in   
  ### SSL certificate settings
   - `minio_enable_ssl` - Switching on secure connection   
      default: `True`
   - `minio_ssl_key_file_name` - Private key file name   
       default: `private.key`
   - `minio_ssl_cert_file_name` - Certificate file name   
      default: `public.crt`
   -  `minio_local_certs` - To find prepared certificate files on ansible host   
       default: `True`
   - `minio_local_key_path` - Prepared private key file path   
      default: `'{{ role_path }}/files/{{ minio_ssl_key_file_name }}'`
   - `minio_local_cert_path` - Prepared certificate file path   
       default: `'{{ role_path }}/files/{{ minio_ssl_cert_file_name }}'`
   - `minio_ca_domain` - Certificate domain (to create certificate if not exists)   
      default: `'{{ minio_hostname }}'`
# https://docs.ansible.com/ansible/latest/openssl_certificate_module.html
   - `minio_ssl_certificate_provider` - Certificater provider (to create certificate if not exists)   
      default: `selfsigned`
   - `minio_ssl_key_size` - Private key encryption size (to create certificate if not exists)   
      default: `4096`
   - `minio_key_path` - The path where key should be placed   
      default: `'{{ minio_home }}/.minio/certs'`
   - `minio_cert_path` - : The path where key should be placed'   
      default: `{{ minio_home }}/.minio/certs'`


Example Playbook
----------------

```yml
- name: Install Minio storage server
  hosts: minio
  roles:
    - role: ansible-role-minio
  vars:
    minio_access_key: EH3FJ946FA17VFAPAQVB
    minio_secret_key: WiiS0bcJf+jxqgPJkDJT2tGvFbpyCS9E+FipKwO7
```

License
-------
Apache

Author Information
------------------

authors:
  - Lean Delivery Team <team@lean-delivery.com>
