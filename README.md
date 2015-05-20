# Ansible Role: OpenSSL

[![MIT License](http://img.shields.io/badge/license-MIT-003399.svg)](http://opensource.org/licenses/MIT)

An Ansible role that manages SSL certificates on Ubuntu 14.04

## Requirements

None

## Role Variables

Ansible variables are listed here along with their default values:

`openssl_self_signed` is a list of self-signed certificate configurations. Each
entry in the list may designate:

* **name** *required*
* **days** (default is 3650)
* **bits** (default is 2048)
* **country** (default is omitted)
* **state** (default is omitted)
* **city** (default is omitted)
* **organization** (default is omitted)
* **unit** (default is omitted)
* **domains** a list of domains (default is omitted)
* **email** (default is omitted)

By default, no self-signed certificates are used:

    openssl_self_signed: []

`openssl_import_keys` is a list of private key information. Each entry in the
list may designate:

* **name** basename for the file *required*
* **content** content of the file *required*

By default, no certificate keys are imported:

    openssl_import_keys: []

`openssl_import_certs` is a list of certificate information. Each entry in the
list may designate:

* **name** basename for the file *required*
* **content** content of the file *required*

By default, no certificates are imported:

    openssl_import_certs: []

`openssl_keys_path` sets the directory for storing private keys.

    openssl_keys_path: "/srv/ssl/private"

`openssl_certs_path` sets the directory for storing certificates.

    openssl_certs_path: "/srv/ssl/certs"

## Dependencies

None

## Example Playbook

    ---
    - hosts: all
      vars:
      - openssl_self_signed:
        - name: "application"
          domains: ["application.com"]
      roles:
      - novuso.openssl

## License

This is released under the [MIT license](http://opensource.org/licenses/MIT).
