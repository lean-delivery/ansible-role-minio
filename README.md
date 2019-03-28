minio role
=========
[![License](https://img.shields.io/badge/license-Apache-green.svg?style=flat)](https://raw.githubusercontent.com/lean-delivery/ansible-role-minio/master/LICENSE)
[![Build Status](https://travis-ci.org/lean-delivery/ansible-role-minio.svg?branch=master)](https://travis-ci.org/lean-delivery/ansible-role-minio)
[![Build Status](https://gitlab.com/lean-delivery/ansible-role-minio/badges/master/build.svg)](https://gitlab.com/lean-delivery/ansible-role-minio/pipelines)
[![Galaxy](https://img.shields.io/badge/galaxy-lean__delivery.minio-blue.svg)](https://galaxy.ansible.com/lean_delivery/minio)
![Ansible](https://img.shields.io/ansible/role/d/role_id.svg)
![Ansible](https://img.shields.io/badge/dynamic/json.svg?label=min_ansible_version&url=https%3A%2F%2Fgalaxy.ansible.com%2Fapi%2Fv1%2Froles%2Frole_id%2F&query=$.min_ansible_version)

This role:
  - installs Minio server on Ununtu, Centos7, RHEL7
  - enables miniio service to systemd

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
