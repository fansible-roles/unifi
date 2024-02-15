Unifi Network Application Quadlet
=========

Deploy the Unifi Network Application as Self Hosted using Podman Quadlet
containers.  

This project implements an Ansible Automation to deploy the mongoDB and Unifi
Network Application using the [Linux Server
Containers](https://github.com/linuxserver/docker-unifi-network-application)

Requirements
------------

* `containers.podman`

Role Variables
--------------

* `unifi_netapp_quadlet`: (`dict`) define the image and tag to for the unifi
  container.  
* `unifi_netapp_quadlet_env`: (`dict`) Define environment variables to be used
  on the container.  
* `unifi_netapp_quadlet_volumes`: (`list`) A list of volumes and paths to be
  monted on the container.  
* `unifi_netapp_mongodb_quadlet_volumes`: (`list`) A list of volumes to be
  mounted on the mongoDB container.  
* `unifi_netapp_mongo_quadlet`: (`dict`) Define the MongoDB container image and
  ta to used.  
* `unifi_netapp_mongodb`: (`str`) The mongoDB database name  
* `unifi_netapp_mongodb_user`: (`str`) The mongodb username  
* `unifi_netapp_mongodb_pass`: (`str`) The mongoDB password

#### Uninstall Flags

Uninstall flags only work when running your playbook with the `uninstall` tag.

* `unifi_netapp_purge`: (`bool`) Remove mongo and unifi volumes, and all it's
  data. (default: `false`)

Dependencies
------------

None

Example Playbook
----------------

* Minimal Example:  

```yaml
- name: Deploy Unifi With Defaults
  hosts: all
  gather_facts: false
  roles:
    - unifi
```

* Uninstalling example:

```yaml
- name: Uninstall Unifi With Defaults
  hosts: all
  gather_facts: false
  roles:
    - unifi
```

Trigger the uninstall playbook with:  

```bash
ansible-playbook playbook.yml --tags uninstall
```

* Uninstall and pruge all volumes:  

```yaml
- name: Deploy Unifi and Remove all Data
  hosts: all
  gather_facts: false
  unifi_netapp_purge: true
  roles:
    - unifi
```

Trigger the uninstall playbook with:  

```bash
ansible-playbook playbook.yml --tags uninstall
```

Developing and Testing
----------------------

This role was developed using [ansible
molecule](https://ansible.readthedocs.io/projects/molecule/).
The use of molecule is optional but recommended.  
  
* Testing:  
Unit tests for checking code regression are available in the [`tests` directory](tests/).
use the `verify` or `test` commands, e.g:  

```bash
molecule test
```

while developing use `verify` instead:  

```bash
molecule create
molecule verify
```

License
-------

[GPL-2.0-or-later](https://spdx.org/licenses/GPL-2.0-or-later.html)

Author Information
------------------

@mrbrandao - Igor Brandão
