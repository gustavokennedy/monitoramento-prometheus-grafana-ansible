# Prometheus with Grafana using Ansible - for Overall.Cloud

Repo por monitoring Overall.Cloud server clients. Configurating prometheus, node_exporter, alertmanager and Grafana. We setup Grafana dashboard which can use source as Prometheus.

## Getting Started

Step 1: Update ip address of instances in inventory file.

Step 2: Run ansible command to setup prometheus, node_exporter, alertmanager and Grafana services

Ansible command: ansible-playbook playbook.yml
