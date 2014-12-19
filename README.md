# Ansible Role For A Base Linux System

[![Build Status](http://img.shields.io/travis/crushlovely/ansible-linux-base.svg?style=flat)](https://travis-ci.org/crushlovely/ansible-linux-base)
[![Current Version](http://img.shields.io/github/release/crushlovely/ansible-linux-base.svg?style=flat)](https://galaxy.ansible.com/list#/roles/1180)

This Ansible role that installs `nginx` and its dependencies:

* `libpcre3`
* `libpcre3-dev`
* `libgd2-xpm-dev`
* `libgeoip-dev`
* `libpam0g-dev`
* `zlibc`
* `zlib1g`
* `zlib1g-dev`

This role requires self-signed certs placed in `files/self_ssl` or legitamite certs placed in `{{ app_name }}/files/ssl/` (found in the root of the ansible roles directory).

Finally it sets the default timezone for the server.  We use this as the base image for all our Ruby and Node.js applications.

## Installation

``` bash
$ ansible-galaxy install crushlovely.nginx
```

## Variables

``` yaml
nginx_version: 1.4.4
app_name: **name of your app**
upstream_port: 8080
```

## Usage

Once this role is installed on your system, include it in the roles list of your playbook.

``` yaml
---
- hosts: localhost
  roles:
    - { role: crushlovely.nginx }
```

## Dependencies

None

## License

MIT