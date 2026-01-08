# Role create-vm

Ansible role to provision multiples Proxmox VMs by cloning from a template.


## Requirements

- Proxmox VE with API access
- Cloud-init enabled template
- `community.proxmox` collection
  - Installed with : `ansible-galaxy collection install -r requirements.yml`
  - Auto-installed with CI/CD in `.github/workflows/ci.yml`
- No dependencies


## Role Variables

`defaults/main.yml` :

| Variable | Default | Description |
|----------|---------|-------------|
| `clone_id` | `200` | Template VM ID to clone from |
| `proxmox_storage` | `local-lvm` | Storage target |
| `proxmox_node` | `proxmox` | Where VMs are created |


### VM Inventory

Define your VMs in `group_vars/all.yml`:
```yaml
vms:
  - name: vm-web01
    vmid: 100
    state: to_create  # or 'created' to skip
    ip: 192.168.1.10  # required
    cores: 2          # optional, defaults to 1
    memory: 2048      # optional, defaults to 1024
```

## License
MIT