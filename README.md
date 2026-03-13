# Ansible K8s IaC Tool

[![Ansible Galaxy](https://img.shields.io/badge/galaxy-somaz94.ansible__k8s__iac__tool-blue.svg)](https://galaxy.ansible.com/ui/repo/published/somaz94/ansible_k8s_iac_tool/)
[![Molecule Test](https://github.com/somaz94/ansible-k8s-iac-tool/actions/workflows/molecule-test.yml/badge.svg)](https://github.com/somaz94/ansible-k8s-iac-tool/actions/workflows/molecule-test.yml)
[![GitHub tag](https://img.shields.io/github/v/tag/somaz94/ansible-k8s-iac-tool)](https://github.com/somaz94/ansible-k8s-iac-tool/tags)
[![License](https://img.shields.io/github/license/somaz94/ansible-k8s-iac-tool)](LICENSE)

An Ansible collection for automating the installation and configuration of Kubernetes and IaC (Infrastructure as Code) tools.

<br/>

## Included Roles

| Role | Description |
|------|-------------|
| `install_kubectl` | Install and configure kubectl |
| `install_krew` | Install krew (kubectl plugin manager) |
| `install_krew_plugins` | Install specified krew plugins |
| `install_helm` | Install Helm package manager |
| `install_terraform` | Install HashiCorp Terraform |
| `install_packer` | Install HashiCorp Packer |
| `install_vagrant` | Install HashiCorp Vagrant |
| `install_kustomize` | Install Kustomize |
| `install_pulumi` | Install Pulumi |
| `setup_bashrc` | Configure shell completions and PATH |

<br/>

## Requirements

- Ansible 2.9+
- Supported OS: Debian/Ubuntu, RHEL/CentOS

<br/>

## Installation

```bash
ansible-galaxy collection install somaz94.ansible_k8s_iac_tool
```

<br/>

## Usage

### Variables

Define variables in `vars.yml`:

```yaml
home_user: "somaz"
krew_version: "v0.4.4"
krew_plugins:
  - ctx
  - neat
  - ns
  # See: https://krew.sigs.k8s.io/plugins/
```

| Variable | Description | Default |
|----------|-------------|---------|
| `home_user` | Target user for tooling setup | - |
| `krew_version` | Krew version to install | `v0.4.4` |
| `krew_plugins` | List of krew plugins to install | `[]` |

<br/>

### Running Locally

```yaml
# site.yml
---
- hosts: localhost
  become: true
  vars_files:
    - vars.yml
  collections:
    - somaz94.ansible_k8s_iac_tool
  roles:
    - setup_bashrc
    - install_kubectl
    - install_krew
    - install_krew_plugins
    - install_terraform
    - install_packer
    - install_vagrant
    - install_helm
    - install_kustomize
    - install_pulumi
```

```bash
ansible-playbook site.yml
```

<br/>

### Running Remotely

```ini
# inventory.ini
[servers]
my-server ansible_ssh_user=somaz ansible_ssh_private_key_file=~/.ssh/id_rsa
```

```yaml
# site.yml
---
- hosts: servers
  become: true
  vars_files:
    - vars.yml
  collections:
    - somaz94.ansible_k8s_iac_tool
  roles:
    - setup_bashrc
    - install_kubectl
    - install_krew
    - install_krew_plugins
    - install_terraform
    - install_packer
    - install_vagrant
    - install_helm
    - install_kustomize
    - install_pulumi
```

```bash
ansible-playbook -i inventory.ini site.yml
```

<br/>

### Post-Task

After the playbook completes, reload the shell configuration:

```bash
source ~/.bashrc
```

<br/>

## Development

### Prerequisites

- Python 3.x
- Docker (for Molecule testing)

### Quick Start

```bash
make venv                          # Create venv and install dependencies
make test                          # Full molecule test (default: ubuntu2004)
make test DISTRO=centos8           # Test with CentOS
make converge                      # Apply roles only
make verify                        # Run verification only
make destroy                       # Destroy test instances
make lint                          # Run ansible-lint
make build                         # Build Galaxy collection
make publish GALAXY_API_KEY=xxx    # Publish to Ansible Galaxy
make clean                         # Remove venv and build artifacts
```

<br/>

## License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.
