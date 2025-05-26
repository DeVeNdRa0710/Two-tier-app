# Two-Tier Flask Notes App with MySQL

This project is a simple two-tier application that allows users to store and manage notes. It consists of a Flask-based web application and a MySQL database. The app is containerized using Docker and orchestrated using Kubernetes.

## 🧱 Architecture Overview

- **Frontend & Backend**: Flask application to create, read, and delete notes.
- **Database**: MySQL to persist notes data.
- **Containers**: Each component runs in its own Docker container.
- **Docker Network**: Connects Flask app and MySQL container.
- **Volumes**: Ensures MySQL data persistence using a local disk volume.
- **Kubernetes Manifests**:
  - Deployments for `notes-app` and `mysql`
  - Services to expose internal and external access
  - ConfigMaps and Secrets for configuration management
  - Namespaces for environment separation

## 🐳 Docker Setup

### 1. Build Docker Image for Flask App

```bash
docker build -t notes-app:latest .
```

### 2. Create Docker volume of name mysql-data
```bash
docker create volume mysql-data
```

### 3. Create Docker network of name two-tier
```bash
docker create network two-tier bridge
```

### 4. Run both container mysql and two-tier app
```bash
docker compose up
```