# CLAUDE.md - ansible-k8s-iac-tool

Ansible collection that automates installation of Kubernetes and IaC tools for Linux systems.

## Commit Guidelines

- Do not include `Co-Authored-By` lines in commit messages.
- Do not push to remote. Only commit. The user will push manually.

## Project Structure

- **Language**: YAML (Ansible playbooks/roles)
- **Type**: Ansible Galaxy collection (`somaz94.ansible_k8s_iac_tool`)
- 10 roles: kubectl, Helm, Terraform, Packer, Vagrant, Kustomize, Pulumi, krew, shell config
- Multi-distro: Ubuntu 22.04+, Debian 11+, Rocky Linux 9+

## Key Directories

- `roles/` — 10 reusable Ansible roles
- `molecule/` — Test scenarios per role
- `meta/` — Galaxy collection metadata

## Build & Test

```bash
make venv                    # Create virtualenv + install deps
make test                    # Run Molecule tests (default: ubuntu2204)
make test DISTRO=rockylinux9 # Test on specific distro
make lint                    # Run ansible-lint
make build                   # Build collection archive
make publish                 # Publish to Ansible Galaxy
```

## Usage

```bash
ansible-galaxy collection install somaz94.ansible_k8s_iac_tool
ansible-playbook site.yml
```

## Language

- Communicate with the user in Korean.
- All documentation and code comments must be written in English.
