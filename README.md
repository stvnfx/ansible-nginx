# Ansible Role For NGINX

[![Current Version](https://img.shields.io/badge/Release-v1.0.0-brightgreen.svg?style=flat)](https://github.com/crushlovely/ansible-nginx/releases)
[![Current Version](http://img.shields.io/github/release/crushlovely/ansible-nginx.svg?style=flat)](https://github.com/crushlovely/ansible-nginx)

This Ansible role that installs `nginx` and its dependencies:

* `libpcre3`
* `libpcre3-dev`
* `libgd2-xpm-dev`
* `libgeoip-dev`
* `libpam0g-dev`
* `zlibc`
* `zlib1g`
* `zlib1g-dev`

This role requires self-signed certs placed in `files/ssl` or third-party certs placed in `{{ app_name }}/files/ssl/` (found in the root of the ansible roles directory).

Finally it sets the default timezone for the server.  We use this as the base image for all our Ruby and Node.js applications.

## Installation

``` bash
$ ansible-galaxy install crushlovely.nginx, v1.0.0
```

## Variables

``` yaml
app_name: **name of your app**
nginx:
  version: 1.6.2
  upstream_port: 8080
  domains:
    - "domain.com"
```

## Usage

Once this role is installed on your system, include it in the roles list of your playbook.

``` yaml
- hosts: localhost
  roles:
    - { role: crushlovely.nginx, nginx.ssl: 'true', nginx.passenger: 'true', nginx.custom: 'true' }
```
You can also add a vars folder to your project folder and have your variables served by adding them to a file and calling it in your playbook.

```yaml
- hosts: localhost
...
  vars_files:
    - vars/default_vars.yml
...
```

## Dependencies

None

## License

MIT