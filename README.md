# MongoDB Configuration Files

This repository contains YAML configuration files for setting up MongoDB and related services. These files are used to configure MongoDB with `mongo-express`, manage secrets, and initialize the database. Below is a description of each file and its purpose.

## Files Overview

### 1. `mongo-config.yaml`

This file contains the basic configuration settings for the MongoDB instance. It defines the MongoDB container settings, environment variables, and volumes required for persistent data storage.

### 2. `mongo-express.yaml`

This configuration file defines the setup for `mongo-express`, a web-based interface for MongoDB. It allows you to manage and view the contents of your MongoDB database through a web browser.

- It connects to the MongoDB instance configured in `mongo-config.yaml`.
- Specifies the port, credentials, and other necessary configurations to make the web interface accessible.

### 3. `mongo-secret.yaml`

This file defines Kubernetes secrets that are required for MongoDB authentication. It contains sensitive information such as database credentials. These secrets are referenced in the MongoDB configuration and `mongo-express.yaml` to ensure secure access.

- The secrets include the MongoDB admin user credentials (username and password).
- The secrets are securely stored and accessed by Kubernetes during deployment.

### 4. `mongoDB.yaml`

This file defines the deployment for MongoDB in a Kubernetes environment. It sets up the MongoDB container, exposes the database service, and configures persistent volumes for storing data. It also references the secrets defined in `mongo-secret.yaml` for secure access.

## Usage Instructions

### 1. Set Up Kubernetes Cluster
Ensure you have a running Kubernetes cluster and have access to the `kubectl` command-line tool.

### 2. Apply the Configuration Files

To deploy MongoDB and related services on your Kubernetes cluster, apply the configuration files in the following order:

```bash
kubectl apply -f mongo-secret.yaml
kubectl apply -f mongo-config.yaml
kubectl apply -f mongoDB.yaml
kubectl apply -f mongo-express.yaml
