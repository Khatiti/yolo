## Deployment with Ansible and Vagrant

This project automates the provisioning, deployment, and management of an e-commerce web application using Ansible and Vagrant. The objective is to deploy a pre-built e-commerce application within a consistent environment, utilizing Docker containers for scalability and ease of management.

### Project Objectives

-  **Automated Environment Setup** : The project aims to create a fully automated environment where the web application, database, and other necessary services are provisioned and deployed with minimal manual intervention.
-  **Separation of Services** : Using Docker, each component of the application (frontend, backend, database) is deployed in its own container. This approach ensures that each service can be independently managed, updated, or scaled.
-  **Modularity and Reusability** : With Ansible roles, each component setup is modular, making it easy to maintain, reuse, and adapt for other similar applications.
-  **Consistent Deployment** : By using Vagrant to provision a virtual machine and Ansible to handle configuration, we achieve a repeatable and consistent deployment process across different environments.

### Project Structure

The project is organized into separate Ansible roles, each handling a specific component's setup, configuration, and deployment. The following roles are used:

* Frontend Role:
 - Pulls the Docker image for the frontend application.
 - Configures and runs the frontend Docker container, exposing it on port 3000.
 - Ensures that any frontend dependencies are installed.

* Backend Role:
 - Pulls the backend Docker image and runs the container on port 5000.
 - Links the backend container to MongoDB for database operations.

* MongoDB Role:
 - Pulls and configures a MongoDB Docker container.
 - Sets up persistent storage by mapping a host directory to MongoDB's data storage directory.
 - Exposes MongoDB on port 27017, allowing the backend to connect seamlessly.


### Technologies Used

- **Vagrant**: Used to create a virtual machine that simulates a consistent environment across various development systems.
- **Ansible**: Manages the configuration and setup of each service using roles, variables, and tasks, ensuring an organized and reproducible setup.
- **Docker**: Each application component is deployed in a Docker container, making it easy to manage, isolate, and scale services.
- **Node.js**: Depending on the application stack, the project installs runtime dependencies for the frontend and backend.
- **MongoDB**: A NoSQL database used to store application data persistently

### Technologies Used

* Provisioning with Vagrant: Vagrant initializes an Ubuntu virtual machine as the deployment environment.
* Configuration with Ansible:
 - Ansible runs the main playbook, which sequentially executes each role.
 - The playbook installs required dependencies, pulls images, and configures each component in Docker containers.
* Application Deployment:
 - The frontend and backend containers are set up and connected to MongoDB.
 - Ansible verifies that each component is correctly deployed and accessible on their respective ports.
* Testing and Verification:
 - Once deployed, the application is accessible in a web browser.
 - Users can verify the application by interacting with it, testing features like “Add Product” to ensure backend and database integration.


 ### Instructions for Use

* Clone the Repository: Ensure you have access to the repository and clone it to your local machine.
* Launch Vagrant:
 - Navigate to the project directory.
 - Run `vagrant up` to provision the virtual machine.
* Run the Ansible Playbook:
 - Once the VM is up, SSH into it using `vagrant ssh`.
 - Run the Ansible playbook with `ansible-playbook playbook.yml` to deploy the application.