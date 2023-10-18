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

```bash
roles:
  - somaz94.ansible-k8s-iac-tool/roles/install_krew
  - somaz94.ansible-k8s-iac-tool/roles/install_krew_plugins
  - somaz94.ansible-k8s-iac-tool/roles/setup_bashrc
```
