Google Cloud CLI
=========

Ansible role to install [Google Cloud CLI](https://cloud.google.com/sdk/docs/install) linux. 
Forked from [labasubagia.gcloud](https://github.com/labasubagia/ansible-role-gcloud) but heavily re-scripted.

> This is installs using standard install method on GCloud website. Installs system wide (for all users).

Requirements
------------
- Ansible Core >= 2.16
- Tested Linux Distribution
  - Debian 12
  - Ubuntu 24.04
  - Fedora 40

> Note: Other (and/or newer) distributions likely to work but not been tested

Role Variables
--------------

The following variables will change the behavior of this role (default values are shown below):

```yaml
## google recommends to install gcloud sdk in user directory, not as root
gcloud_additional_components: []
```

Test Locally using Lint and Ansible Molecule
--------------------------------------------

```
rm -rf ~/.ansible/roles/
molecule test --all
molecule test --all --driver-name=podman
molecule test --all -d docker

yamllint -v . && ansible-lint -v . && molecule test --all

tox
tox -p auto   # Runs tox environments in parallel, depending on local cpu core count and depends clause.
tox -e lint   # Runs only lint tox environment
tox -e fedora40  # Runs only fedora40 tox environment, if it depends on another tox environment, that should also execute.
```


Example Playbook
----------------
```yaml
- hosts: servers
  roles:
    - role: hammadrauf.gcloud
      vars:
        gcloud_additional_components:
          - gke-gcloud-auth-plugin
          - kubectl
```

License
-------

MIT

Author Information
------------------

[Laba Subagia](https://github.com/labasubagia)
  
This Forked maintained by [Hammad Rauf](https://github.com/hammadrauf)