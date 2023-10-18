# Role: install_krew & install_krew_plugins

This role installs and sets up `install_krew` and `install_krew_plugins for Kubernetes tooling.

## Requirements

- Ansible 2.9 or higher
- Targeted OS: Deiban/Ubuntu, RHEL/CentOS (For now)

## Role Variables

Update the variables as required in `~/vars.yml`:

```bash
home_user: "" # home_user
krew_version: "v0.4.4"
krew_plugins:
  - "ctx"
  - "neat"
  - "ns"
```

## Dependencies

None.

## Example

To use this role, include it in your playbook as follows:

### local
```bash
# site.yml
---
- hosts: localhost
  become: yes
  vars_files:
    - ~/vars.yml
  collections:
    - somaz94.ansible_k8s_iac_tool
  roles:
    - install_krew
    - install_krew_plugins
    - setup_bashrc
```

### Remote
```bash
# site.yml
---
- hosts: <hosts> # Remote Server
  become: yes
  vars_files:
    - ~/vars.yml
  collections:
    - somaz94.ansible_k8s_iac_tool
  roles:
    - install_krew
    - install_krew_plugins
    - setup_bashrc
```
