kapa-secureserver
=========

Role for installing Secure Server for X-Road (Kansallinen Palveluväylä).

Requirements
------------

Ubuntu 14.04 or later on target machine. Transmitting the superuser password as
private variable requires the `python-passlib` package.

Role Variables
--------------

- `xroad_admin_fqdn` - FQDN for the admin Web UI certificate.
- `xroad_service_fqdn` - FQDN for the service certificate. If uncertain, use
   same as xroad_admin_fqdn.
- `xroad_superuser_password` - Recommended to prompt in playbook, see
   example below.

Dependencies
------------

N/A

Example Playbook
----------------

- hosts: all
  sudo: true
  vars_prompt:
  - name: "xroad_superuser_password"
    prompt: "Please enter password for X-Road superuser"
    private: yes
    encrypt: "sha512_crypt"
    confirm: yes
  roles:
    - role: kapa-secureserver

License
-------

BSD

Author Information
------------------

https://forgeservicelab.fi
