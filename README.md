# Ansible Collection - chadmf.patching

This collection provides roles for RHEL system patching with pre/post checks and automated reboots.

## Roles

### patch_rhel

Patches RHEL systems using DNF with the following features:
- Pre-check for available disk space
- Update all packages to latest versions
- Automatic reboot if kernel/glibc updated
- Post-check to verify system uptime
- Summary logging of updates

## Installation

```bash
ansible-galaxy collection install chadmf.patching
```

Or install from GitHub:

```bash
ansible-galaxy collection install git+https://github.com/chadmf/ansible-collection-patching.git
```

## Usage

```yaml
---
- name: Patch RHEL systems
  hosts: all
  become: true
  roles:
    - patch_rhel
```

Or use with tags to run specific tasks:

```bash
ansible-playbook patch.yml --tags patching
ansible-playbook patch.yml --tags precheck,postcheck
```

## Tags

| Tag | Description |
|-----|-------------|
| `precheck` | Disk space verification |
| `patching` | DNF package updates |
| `check` | Reboot requirement check |
| `reboot` | System reboot |
| `postcheck` | Uptime verification |
| `log` | Update summary |

## Requirements

- RHEL 8+ or compatible (Rocky, Alma, CentOS Stream)
- `needs-restarting` command available (from `dnf-utils` or `yum-utils`)

## License

GPL-3.0-or-later
