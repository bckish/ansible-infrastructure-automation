# Ansible Infrastructure Automation

An original, reusable Ansible baseline for configuring Linux application hosts. It installs
Nginx, writes a health endpoint, and applies a small hardened Nginx configuration. The project
is intentionally safe to explore locally: its example inventory uses placeholder hostnames and
does not contain credentials.

## What it demonstrates

- Inventory and group variables
- Idempotent role-based automation
- Package, service, template, and file management
- Check mode and syntax validation before a real deployment

## Prerequisites

- Ansible Core 2.14+
- SSH access to a Debian/Ubuntu target with a sudo-capable account

## Run locally

Copy and edit the example inventory; do not commit private IP addresses or keys.

```bash
cp inventory/hosts.example.ini inventory/hosts.ini
ansible-playbook --syntax-check -i inventory/hosts.ini playbooks/site.yml
ansible-playbook --check -i inventory/hosts.ini playbooks/site.yml
ansible-playbook -i inventory/hosts.ini playbooks/site.yml
```

## Repository layout

```text
inventory/       example target inventory
group_vars/      non-secret defaults
playbooks/       deployment entry points
roles/nginx/     reusable web-server role
```

## Security note

Keep real secrets in Ansible Vault or a CI secret store. The included inventory is an example
only and the project never provisions cloud resources by itself.
Reusable Ansible roles for Nginx, MongoDB, backups, and operations.
