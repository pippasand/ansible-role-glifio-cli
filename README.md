glif.io CLI
===========

Ansible tooling to automatically build and install the Glif.io CLI. 

Currently supports building from source, future versions will also support installing official binaries from Glif.

To run without a dedicated playbook, simply edit the included inventory file, install the required roles by running `ansible-galaxy install -r requirements.yml`, then run `ansible-playbook install.yml`. Advanced users can override the role variables as required.

(If you don't have Ansible yet, install it using your favourite method such as pip, brew, apt, etc.)

Supported Platforms
-------------------

This role is tested to work on the latest stable and oldstable versions of Ubuntu (LTS, previous LTS) as well as Debian, but should work on any standard Linux distribution including WSLv2. If you run into any issues, let us know at ghost@glif.io.

macOS support is in the works and will be coming soon.

Requirements
------------

* Git
* Ansible
* Go/Golang (will automatically be installed by the `gantsign.golang` role) installed to /opt/go/$GOLANG_VERSION.

Role Variables
--------------

Available variables are listed below, along with default values (see defaults/main.yml):

`install_method: "git"`

What method to use to install the Glif CLI
Accepts "git", will soon also accept "binary"

`glif_cli_version: "v1.0.0"`

Version of the Glif CLI to install

```
glif_users:
  - "lotus"
```

A list of users to configure the Glif CLI for.

`use_calibrationnet: true`

Whether to build for calibrationnet or mainnet.
Defaults to calibnet for now, will default to mainnet later.

Dependencies
------------

`gantsign.golang` role - use `ansible-galaxy install -r requirements.yml` to install it.

Example Playbook
----------------

```
---
# Install the Glif.io CLI
- name: Install glif cli
  hosts: glif
  become: true

  vars:
    golang_version: 1.20.7

  roles:
    - role: glifio.cli
```

License
-------

Creative Commons Zero v1.0 Universal

Author Information
------------------

Inigo Montoya (@ghost@glif.io)