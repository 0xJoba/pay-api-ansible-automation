# Pay-API Infrastructure Automation

This repository contains Ansible playbooks and roles to automate the deployment of a multi-node environment for the `pay-api` microservice. It configures a database backend and multiple web server frontends.

## Project Architecture
- **1 Database Node (RedHat/CentOS):** Installs and configures MariaDB.
- **3 Web Nodes (RedHat/CentOS):** Installs Apache (`httpd`) and deploys a dynamic welcome page.

## Assignment Tasks Completed
- [x] **Task 1: Database Role** - Created a dedicated role to install and start MariaDB.
- [x] **Task 2: Variables** - Centrally managed configuration using `group_vars/all`.
- [x] **Task 3: Templates** - Implemented a Jinja2 template (`index.html.j2`) to display dynamic system and database metadata.
- [x] **Task 4: Handlers & Idempotency** - Configured handlers to restart services only when configuration changes.

## Prerequisites
- Ansible installed on your Control Node.
- SSH access to target EC2 instances.
- A valid `inventory.yml` file containing `dbservers` and `webservers` groups.

## Variable Configuration
The environment is customized via `group_vars/all`. Key variables include:
- `db_name`: The name of the database (e.g., `payapi_staging`).
- `db_port`: The port the database listens on (e.g., `3306`).
- `app_version`: The current version of the application.

## How to Run
To execute the playbook and configure the infrastructure, run:

```bash
ansible-playbook -i inventory.yml pay-api.yaml
