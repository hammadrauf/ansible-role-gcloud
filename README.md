Google Cloud CLI
=========

Ansible role to install [Google Cloud CLI](https://cloud.google.com/sdk/docs/install) linux. 
Forked from [labasubagia.gcloud](https://github.com/labasubagia/ansible-role-gcloud)

> Recommended to install inside home user directory (by official documentation) as non-root

Requirements
------------
- Ansible Core >= 2.16
- Tested Linux Distribution
  - Debian 12
  - Ubuntu 24.04
  - Fedora 40

> Note: Other distributions likely to work but not been tested

Role Variables
--------------

The following variables will change the behavior of this role (default values are shown below):

```yaml
## google recommends to install gcloud sdk in user directory, not as root
gcloud_install_dir: "{{ ansible_env.HOME }}"
gcloud_additional_components: []
gcloud_state: present # present/absent

# For this file you need to make sure it is exists
# Otherwise it will be skipped
gcloud_fish_config: "{{ ansible_env.HOME }}/.config/fish/config.fish"
gcloud_bash_config: "{{ ansible_env.HOME }}/.bashrc"
gcloud_zsh_config: "{{ ansible_env.HOME }}/.zshrc"
```

Test Locally using Ansible Molecule
-----------------------------------
```
 molecule test --all
  molecule test --all --driver-name=podman
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