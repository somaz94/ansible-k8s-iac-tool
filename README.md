# ansible k8s iac tool

This Ansible collection is dedicated to setting up Kubernetes tooling. The collection comprises several roles, each focusing on a specific tool or configuration:

- `install_kubectl`: Sets up kubectl.
- `install_krew`: Sets up krew.
- `install_krew_plugins`: Installs specified krew plugins.
- `install_terraform`: Sets up terraform.
- `install_helm`: Sets up helm.
- `install_packer`: Sets up packer.
- `install_kustomize`: Sets up kustomize.
- `install_pulumi`: Sets up pulumi.
- `install_vagrant`: Sets up vagrant.
- `setup_bashrc`: Adds specific configurations to the bashrc.

<br/>

## Requirements

- Ansible 2.9 or higher
- Targeted OS: Deiban/Ubuntu, RHEL/CentOS (For now)

<br/>

## Example Playbook

### Running Locally

#### 1. Setting Up the Variable File

Define the necessary variables in the `vars.yml` file:
```bash
# vars.yml
home_user: "somaz"
krew_version: "v0.4.4"
krew_plugins:
  - "ctx"
  - "neat"
  - "ns"
  # more... 
```

- For a comprehensive list of available krew plugins, visit the official [krew plugins directory](https://krew.sigs.k8s.io/plugins/).

#### 2. Creating the Playbook

Write the playbook in the `site.yml` file:
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

#### 3. Running the Playbook

Execute the playbook with the following command:
```bash
ansible-playbook site.yml
```

<br/>

### Running Remotely

#### 1. Setting Up the Variable File

Define the necessary variables in the `vars.yml` file:
```bash
# vars.yml
home_user: "somaz"
krew_version: "v0.4.4"
krew_plugins:
  - "ctx"
  - "neat"
  - "ns"
  # more... 
```

#### 2. Setting Up the Inventory File

Define the remote server information and connection details in the `inventory.ini` file:
```bash
# inventory.ini
[test_servers]
test-server ansible_ssh_user=somaz ansible_ssh_private_key_file=/home/somaz/.ssh/id_rsa_somaz94
```

#### 3. Creating the Playbook

Write the playbook in the `site.yml` file:
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

#### 4. Running the Playbook

Execute the playbook with the following command:
```bash
ansible-playbook -i inventory.ini site.yml
```

<br/>

### Post-Task Actions

After the tasks have been completed, apply the changes on the installed machine by running:
```bash
source ~/.bashrc
```
- This command will apply any changes made in the .bashrc file to the current shell session.


<br/>

## Role Variables

The variables below can be modified in the `~/vars.yml` file as per your requirements:

- `home_user`: User for which the tooling setup should be applied. 
- `krew_version`: Desired version of krew. Default: `v0.4.4`
- `krew_plugins`: List of krew plugins to be installed.

<br/>

## Dependencies

None.

<br/>

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

