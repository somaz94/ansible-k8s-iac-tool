# Role: install_setup_bashrc

This role installs and sets up `install_setup_bashrc` for Kubernetes tooling.

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
roles:
  - somaz94.ansible-k8s-iac-tool/roles/setup_bashrc
```