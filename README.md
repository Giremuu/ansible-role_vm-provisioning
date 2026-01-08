# Proxmox VMs Provisioning with Ansible

[![CI](https://github.com/Giremuu/ansible-role_vm-provisioning/actions/workflows/ci.yml/badge.svg)](https://github.com/Giremuu/ansible-role_vm-provisioning/actions/workflows/ci.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

Automated Proxmox multiple VM provisioning through template cloning with cloud-init configuration (IPs, DNS, cores...).

**Training project** for continue to learn Ansible automation and CI/CD best practices with GitHub Actions.


## Features

- Clone multiples VMs from Proxmox templates
- Configure cloud-init (IP, DNS, gateway, CPU, memory...)
- Idempotent operations (skips existing VMs + state "created"/"to_create")
- Automated linting (yamllint, ansible-lint) via CI/CD


## Quick Start
- Install requirements with : `ansible-galaxy collection install -r requirements.yml`
- Configure variables in group_vars (your true vault.yml + all.yml)
- Run playbook : `ansible-playbook playbooks/provision-vms.yml --ask-vault-pass`


## Project Structure
```
.
├── .github/workflows/    # CI/CD pipelines
├── roles/create-vm/      # VM creation role
├── playbooks/            # Ansible playbooks
├── group_vars/           # Variables and credentials
└── requirements.yml      # Ansible dependencies
```


## Configuration

Define your VMs in `group_vars/all.yml`:
```yaml
vms:
  - name: vm-web01
    vmid: 100
    state: to_create
    ip: 192.168.1.10
    cores: 2
    memory: 2048
```

See `group_vars/all-exemple.yml` for full configuration options


## CI/CD

Automated checks on every push / pull:
- YAML syntax validation (yamllint)
- Ansible best practices (ansible-lint)
- Playbook syntax check


## Documentation

- [Role Documentation](roles/create-vm/README.md)
- [Variables Examples](group_vars/)

## License
MIT - see [LICENSE](LICENSE) file.


## Author

Giremuu - [GitHub Profile](https://github.com/Giremuu)
