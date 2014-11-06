ansible-haproxy-keepalived
==========================

A playbook building high availability Load Balancer with HAProxy and keepalived.

## Requirements

- [VirtualBox](https://www.virtualbox.org/wiki/Downloads). Tested on 4.3.x.
- [Vagrant](http://www.vagrantup.com/downloads.html). Tested on 1.6.3
- [Ansible](http://docs.ansible.com/intro_installation.html). Tested on 1.7.1 

## Overview

It will install high availability Load Balancer with HAProxy and keepalived.
You can customize it by edit vars file.
Tested on Ubuntu 14.04 Trusty and CentOS 6.5.

## Usage

- Edit vars/main.yml

- Test on Vagrant virtual machine(Requires Ansible).

```bash
$ vagrant up
```

- Install to remote server.

Edit `ansible_hosts`.

```
default ansible_ssh_host=xxx.xxx.xxx.xxx ansible_ssh_port=22
```

Run playbook.

```bash
ansible-playbook site.yml -i ansible_hosts
```

## vars

```vars/main.yml
haproxy_user: haproxy
haproxy_major_version: 1.5
haproxy_minor_version: 8
haproxy_download_url: "http://www.haproxy.org/download/{{ haproxy_major_version }}/src/haproxy-{{ haproxy_major_version }}.{{ haproxy_minor_version }}.tar.gz"
haproxy_src_dir: /tmp
haproxy_make_option: TARGET=linux2628 CPU=x86_64 USE_OPENSSL=1 USE_ZLIB=1 USE_PCRE=1
```

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
