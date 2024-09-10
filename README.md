# Polkadot Node Setup with Reverse Proxy

This repository provides Ansible playbooks for setting up a Polkadot full node and configuring an Nginx reverse proxy.

## Prerequisites

- Ansible installed on your local machine.
- Access to an Ubuntu server where you will run the playbooks.
- SSH access to the remote server with the private key file (`luganodes.pem`).

## Setup

1. **Clone the Repository**

   ```bash
   git clone https://github.com/mohammadshaad/luganodes-assignment.git
   cd luganodes-assignment
   ```

2. **Update Inventory File**

   Edit `inventory.ini` to match your server details:

   ```ini
   [node1]
   node1 ansible_host=[your-host] ansible_ssh_user=ubuntu ansible_ssh_private_key_file=[.pem file path]
   ```

3. **Setup Polkadot Full Node**

   Run the Ansible playbook to set up the Polkadot full node:

   ```bash
   ansible-playbook -i inventory.ini polkadot_setup.yml
   ```

4. **Setup Reverse Proxy**

   Run the Ansible playbook to set up Nginx as a reverse proxy:

   ```bash
   ansible-playbook -i inventory.ini reverse_proxy.yml
   ```

## Playbooks

### `polkadot_setup.yml`

- Installs required packages.
- Downloads the Polkadot binary.
- Starts the Polkadot node with warp sync.

### `reverse_proxy.yml`

- Installs Nginx.
- Configures Nginx to proxy requests to the Polkadot node.
- Enables and restarts Nginx with the new configuration.

## Output
<img width="1440" alt="Screenshot 2024-09-10 at 10 09 16 PM" src="https://github.com/user-attachments/assets/3de5b44b-1f9d-472d-b074-ae8316fb0e38">
