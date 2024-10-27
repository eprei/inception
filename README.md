# Inception

## 📝 Description

Inception is a System Administration project focused on Docker containerization and service orchestration. The project involves creating a small infrastructure composed of different services under specific rules using Docker Compose. Each service runs in a dedicated container built on either Alpine or Debian Linux.

## ⚠️ Important Disclaimers

### Security Notice
This repository contains sensitive information in the `.env` file for educational purposes. In a production environment:
- **NEVER** commit `.env` files or any files containing secrets
- **NEVER** expose database credentials, API keys, or passwords in your repository
- Add `.env` to your `.gitignore` file
- Use secure secret management solutions for production deployments

### Educational Purpose
This project is designed for learning purposes only and is not intended for production use. It demonstrates Docker concepts and container orchestration but may not implement all security best practices required for a production environment.

### WordPress Configuration
Per project requirements, WordPress was configured entirely through command-line interface (CLI) using wp-cli, without accessing the graphical user interface. This approach demonstrates automated WordPress deployment and configuration practices.

## 🛠 Components

The infrastructure consists of three main containers:
- **NGINX**: Web server with TLSv1.2/TLSv1.3 support
- **WordPress + PHP-FPM**: Content Management System
- **MariaDB**: Database server

## 🏗 Architecture

```plaintext
                     ┌─────────────────┐
                     │     NGINX       │
                     │   (Port 443)    │
                     └────────┬────────┘
                              │
                              │
                 ┌────────────┴───────────┐
                 │                        │
        ┌────────┴─────────┐    ┌────────┴─────────┐
        │    WordPress     │    │     MariaDB      │
        │    (Port 9000)   │    │    (Port 3306)   │
        └──────────────────┘    └──────────────────┘
```

## 🔑 Key Features

- **Containerization**: Each service runs in its own Docker container
- **Custom Configurations**: Hand-crafted Dockerfiles and configuration files
- **Secure Communication**: TLS encryption for NGINX
- **Volume Management**: Persistent storage for WordPress files and MariaDB data
- **Network Isolation**: Custom Docker network for inter-container communication
- **Environment Variables**: Secure credential management
- **Automatic Container Recovery**: Containers restart on failure

## 🚀 Getting Started

### Prerequisites

- Docker
- Docker Compose
- Make

### Installation

1. Clone the repository

2. Create necessary directories and start services
```bash
make
```

### Available Commands

- `make`: Create directories and start services
- `make up`: Start services
- `make build`: Build containers
- `make stop`: Stop services
- `make restart`: Restart services
- `make remove`: Remove containers
- `make down`: Stop and remove containers, networks, and images
- `make fclean`: Complete cleanup including volumes
- `make re`: Rebuild entire project

## 📂 Project Structure

```
├── Makefile
└── srcs
    ├── .env
    ├── docker-compose.yml
    └── requirements
        ├── mariadb
        │   ├── Dockerfile
        │   └── conf/
        ├── nginx
        │   ├── Dockerfile
        │   └── conf/
        └── wordpress
            ├── Dockerfile
            └── conf/
```

## ⚙️ Configuration

### Environment Variables
The project uses a `.env` file for configuration. Required variables include:
- Database credentials
- WordPress settings
- Domain name configuration

### Volumes
Two persistent volumes are configured:
- WordPress files: `/home/login/data/wordpress`
- MariaDB data: `/home/login/data/mariadb`

### Networking
- Services communicate through a custom Docker network
- NGINX exposes port 443 (HTTPS)
- Internal services use dedicated ports (MariaDB: 3306, WordPress: 9000)

## 🔐 Security Features

- TLS encryption (v1.2/v1.3)
- Secure environment variable management
- Isolated container network
- No direct database exposure
- Custom user configurations

## 📚 Learning Outcomes

This project teaches:
- Docker containerization
- Service orchestration
- Nginx configuration
- WordPress setup
- Database management
- Network security
- Docker Compose usage
- Infrastructure as Code principles

## ⚠️ Notes

- Containers are built using Alpine Linux 3.16.3
- Each service has its own Dockerfile with specific configurations
- The project follows Docker best practices for daemon management
- Latest tags are not used as per project requirements

## 🛡️ Compliance

This implementation adheres to the 42 school project requirements including:
- Custom Dockerfile creation
- No pre-built images (except base Alpine/Debian)
- Proper volume management
- TLS implementation
