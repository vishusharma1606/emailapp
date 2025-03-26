# db-demo-app

This repository contains the Kubernetes configuration files for deploying and managing the `db-demo-app`.

## Overview

The `db-demo-app` is a demo application designed to connect to a MongoDB database. The deployment includes a Kubernetes Deployment and Service to manage the application and expose it to external traffic.

## Files

- **`deployment-service-db-demo-app.yaml`**: Defines the Deployment and Service for the `db-demo-app`.

## Deployment Instructions

1. Ensure you have a Kubernetes cluster set up and `kubectl` configured to interact with it.
2. Apply the configuration file:
   ```bash
   kubectl apply -f deployment-service-db-demo-app.yaml
   ```
3. Verify the Deployment and Service:
   ```bash
   kubectl get deployments
   kubectl get services
   ```

## Environment Variables

The application uses the following environment variables, which are configured via a ConfigMap:

- **`MONGO_HOST`**: The hostname of the MongoDB server.
- **`MONGO_PORT`**: The port number of the MongoDB server.

## Accessing the Application

The Service is exposed as a LoadBalancer. Use the external IP provided by the Service to access the application on port `3000`.

## Notes

- Ensure the `mongo-config` ConfigMap is created and contains the required keys (`MONGO_HOST` and `MONGO_PORT`).
- Update the `image` field in the Deployment if a new version of the application is available.
