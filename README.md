# Observability Stack Automation (Prometheus, Grafana & Node Exporter)

Automated provisioning and deployment of a modern observability stack using **Vagrant** and **Ansible**. 

This project demonstrates how to bypass OS package manager limitations (which often provide outdated versions) by dynamically downloading official binaries and configuring the operating system to support them securely.

## Technical Highlights

* **Version Pinning:** Installs specific versions of Grafana (10.4.0) and Prometheus (2.51.0) directly from official `.tar.gz` releases to meet strict production requirements.
* **Idempotency:** The Ansible playbook is fully idempotent. Executing it multiple times will not alter the system unless the desired state changes.
* **OS Hardening & Systemd:** Demonstrates advanced Linux administration (RHCSA level) by:
  * Creating dedicated system users (`--system -s /bin/false`).
  * Enforcing correct permissions and ownership.
  * Restoring **SELinux** security contexts (`restorecon`) to allow execution from custom paths.
  * Creating and managing native `systemd` `.service` files.
  * Managing local firewalls with `firewalld`.
* **Configuration as Code:** Replaces default configuration files with declared YAML blocks (`prometheus.yml`) ensuring targets like `node_exporter` are monitored immediately upon deployment.

## Requirements

* [Vagrant](https://www.vagrantup.com/)
* [VirtualBox](https://www.virtualbox.org/) (or libvirt/KVM)
* [Ansible](https://www.ansible.com/)

## Usage

1. **Spin up the infrastructure:**
   ```bash
   vagrant up
   
2. **Run the Ansible Playbook:**
   ```bash
    ansible-playbook -i inventory.ini observability_install.yml

3. **Access the Web Interfaces:**
* Grafana: `http://<VAGRANT_NODE_IP>:3000 (Default login: admin/admin)`
* Prometheus: `http://<VAGRANT_NODE_IP>:9090`
