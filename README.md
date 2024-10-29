# E-commerce Application Deployment with Ansible and Vagrant

This project provisions an environment to deploy an e-commerce web application using Vagrant and Ansible. The setup includes Docker containers for the frontend, backend, and MongoDB services.

## Project Structure

The Ansible playbook and roles are structured to facilitate modular and reusable configuration for different components of the application.

### Directory Structure
- Client: The React frontend.
- Backend: The Node.js server for API handling.
- MongoDB: The database for storing products.

```bash
.
├── client                   # Frontend application 
│   ├── public
│   ├── src
│   ├── dockerfile
│   └── package.json
├── backend                  # Backend application 
│   ├── controllers
│   ├── models
│   ├── routes
│   ├── dockerfile
│   └── package.json
├── docker-compose.yml       # Docker Compose configuration
├── Vagrantfile              # Vagrant configuration file
├── playbook.yml             # Main Ansible playbook
├── vars
│   └── main.yml             # Variable file for reusable configurations
└── roles
│   ├── frontend             # Role to configure the frontend container
│   │   └── tasks
│   │       └── main.yml
│   ├── backend              # Role to configure the backend container
│   │   └── tasks
│   │       └── main.yml
│   └── mongodb              # Role to configure MongoDB container
│       └── tasks
│           └── main.yml
└── README.md                # Project documentation

```

## Requirements
- [Vagrant](https://www.vagrantup.com/downloads) 
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads) 
- [Ansible](https://www.ansible.com/products/ansible) 

## Setup Instructions
### Clone the Repository

```bash
git clone https://github.com/Khatiti/yolo.git,

cd yolo 

```

### Define Variables: Modify vars/main.yml as necessary for your environment.
```bash
# vars/main.yml
repo_url: "https://github.com/Khatiti/yolo"
app_directory: "/var/www/app"
frontend_image: "yolo/client:1.2.0"
backend_image: "yolo/backend:1.2"
mongodb_image: "mongo:6.0"

```

### Run the Vagrant Environment: Use Vagrant to spin up the virtual machine and provision it with Ansible.

```bash
vagrant up

```

### Provision the VM to apply the Ansible playbook manually,

```bash
vagrant provision

```

## Roles and Components
### Frontend Role
- Path: `roles/frontend/tasks/main.yml`
- Description: Sets up the frontend container using Docker. The frontend runs on port `3000`.
- Tags: `frontend`, `frontend_container`


### Backend Role
- Path: `roles/backend/tasks/main.yml`
- Description: Sets up the backend container using Docker. The backend runs on port `5000`.
- Tags: `backend`, `backend_container`


### MongoDB Role
- Path: `roles/mongodb/tasks/main.yml`
- Description: Sets up the MongoDB container with persistent storage and accessible on port `27017`.
- Tags: `mongodb`, `mongodb_container`