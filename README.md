# ansible k8s iac tool

This Ansible role sets up various Kubernetes tooling components including kubectl, krew, krew plugins, and additional packages.

<br/>

## Requirements

- Ansible 2.9 or higher
- Targeted OS: Ubuntu (For now)

<br/>

## Role Variables

The variables below can be modified in the `group_vars/all/vars.yml` file as per your requirements:

- `home_user`: User for which the tooling setup should be applied. Default: `somaz`
- `krew_version`: Desired version of krew. Default: `v0.4.4`
- `krew_plugins`: List of krew plugins to be installed. Defaults:
  - `ctx`
  - `neat`
  - `ns`

<br/>

## Dependencies

None.

<br/>

## Usage

### Applying on Remote Systems

1. Update `inventory.ini` with your remote systems.
2. Run the playbook using:
```bash
ansible-playbook -i inventory.ini site.yml
```

After the tasks have been completed, apply the changes on the installed machine by running:
```bash
source ~/.bashrc
```
- This command will apply any changes made in the .bashrc file to the current shell session.

### Applying on Local System
1. Use the provided inventory.ini.local which is already set to target localhost.
2. Run the playbook using:
```bash
ansible-playbook -i inventory.ini.local site.yml.local
```

After the tasks have been completed, apply the changes on the installed machine by running:
```bash
source ~/.bashrc
```
- This command will apply any changes made in the .bashrc file to the current shell session.

<br/>

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

