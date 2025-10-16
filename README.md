# ansible-beelink-monitoring

Ansible project for deploying Prometheus node_exporter on multiple VMs.

## Environment
- Controller: Rocky Linux 10 (bastion host)
- Targets: Rocky 10 and Ubuntu 22.04 VMs
- Prometheus already installed manually on monitoring VM

## Setup

### Copy project from WSL to Rocky controller:
```bash
scp -r ~/prometheus-ansible user@<rocky-ip>:/home/user/
```

### Run the playbook:
```bash
ansible-playbook -i inventory.yml playbooks/deploy_node_exporter.yml --ask-become
```

## Notes

Prometheus was installed manually via:
```bash
wget https://github.com/prometheus/prometheus/releases/latest/download/prometheus-*.linux-amd64.tar.gz
tar -xzf prometheus-*.linux-amd64.tar.gz
sudo mv prometheus-*/prometheus /usr/local/bin/
sudo mv prometheus-*/promtool /usr/local/bin/
```
(and configured as a systemd service)

## Project Structure
```
.
├── ansible.cfg
├── inventory.yml
├── playbooks/
│   └── deploy_node_exporter.yml
└── README.md
```