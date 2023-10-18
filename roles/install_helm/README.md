# Role: install_helm

This role installs and sets up `install_helm` for Kubernetes tooling. 

## Requirements

- Ansible 2.9 or higher
- Targeted OS: Deiban/Ubuntu, RHEL/CentOS (For now)

## Role Variables

Update the variables as required in `~/vars.yml`:

```bash
home_user: "" # home_user
```

## Dependencies

None.

## Example

To use this role, include it in your playbook as follows:

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
    - install_helm
```
