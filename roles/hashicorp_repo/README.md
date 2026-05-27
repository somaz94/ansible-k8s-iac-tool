# Role: hashicorp_repo

Helper role that configures the HashiCorp apt/dnf package repository (GPG key + repo list / `.repo` file). It does not install any tool — it only makes the HashiCorp repo available so that consumer roles (`install_terraform`, `install_packer`, `install_vagrant`) can install their packages.

<br/>

## Requirements

- Ansible 2.9 or higher
- Targeted OS: Debian/Ubuntu, RHEL/CentOS

<br/>

## Role Variables

| Variable | Default | Description |
|---|---|---|
| `hashicorp_repo_apt_keyring` | `/usr/share/keyrings/hashicorp-archive-keyring.gpg` | Path to the dearmored HashiCorp GPG keyring on Debian/Ubuntu. |
| `hashicorp_repo_apt_list` | `/etc/apt/sources.list.d/hashicorp.list` | Path to the apt sources list entry for the HashiCorp repo. |
| `hashicorp_repo_rhel_url` | `https://rpm.releases.hashicorp.com/RHEL/hashicorp.repo` | Upstream `.repo` URL used on RHEL-family systems. |
| `hashicorp_repo_rhel_file` | `/etc/yum.repos.d/hashicorp.repo` | Destination path for the `.repo` file on RHEL-family systems. |

<br/>

## Dependencies

None. This role is intended to be consumed by other roles via `include_role`.

<br/>

## Example

This role is not used directly in a playbook. Consumer roles include it before their package install task:

```yaml
# roles/install_terraform/tasks/main.yml
---
- name: Configure HashiCorp package repository
  ansible.builtin.include_role:
    name: hashicorp_repo

- name: Install Terraform
  ansible.builtin.package:
    name: terraform
    state: present
```

<br/>

## Supported Platforms

- Debian: `bullseye`, `bookworm`
- Ubuntu: `jammy`, `noble`
- EL: `9`
