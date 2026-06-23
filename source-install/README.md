# Nginx Source Installation with Ansible

## Environment

* Ubuntu
* Nginx Source Build (1.30)
* Header More Module
* libgd
* Systemd

---

## Directory Structure

```text
/usr/local/nginx
├── conf
├── conf.d
├── certs
└── logs
```

---

## Installation Flow

APT Update

↓

Install Required Packages

↓

Upload Source Files

↓

Extract Source

↓

Build libgd

↓

Configure Nginx

↓

make && make install

↓

Deploy nginx.conf

↓

Register systemd Service

↓

Enable nginx

---

## Install Required Packages

```yaml
- name: Install packages
  apt:
    name:
      - build-essential
      - libssl-dev
      - libpcre2-dev
      - zlib1g-dev
```

---

## Source Build

```yaml
- name: Run nginx configure
  shell: ./nginx-configure.sh

- name: make install
  shell: make && make install
```

---

## Deploy Configuration

* nginx.conf
* default.conf
* upstream.conf

---

## Register Service

```yaml
- name: Enable nginx service
  systemd:
    name: nginx.service
    enabled: yes
```
