# Inception

## Overview
The **Inception** project is part of the system administration curriculum and focuses on deepening your understanding of Docker. The goal is to virtualize multiple Docker images and create a personal virtual machine with various services.

## Project Objectives
- Set up a mini-infrastructure using **Docker Compose**.
- Build and configure containers for:
  - **NGINX** with TLSv1.2 or TLSv1.3.
  - **WordPress** with **php-fpm**.
  - **MariaDB**.
- Configure volumes for both the WordPress database and files.
- Ensure all containers run in isolated environments using custom-built Dockerfiles.
- Containers must restart in case of failure, and best practices in Dockerfile writing must be followed.

## Key Constraints
- Use of **Alpine** or **Debian** for container base images.
- Containers must be managed via **Docker Compose** and built with a **Makefile**.
- TLS must be implemented for secure communication via port 443.
- Variables like credentials must be managed securely using **environment variables** and **Docker secrets**.

## Setup Instructions
1. Clone the repository and navigate to the project directory.
2. Run the Makefile to build and start the containers:
   ```bash
   make
