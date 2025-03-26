# db-demo-app

This repository contains the Kubernetes configuration files and Dockerfile for deploying and managing the `db-demo-app`.

## Steps to Deploy

1. **Create a Docker Image**  
   Build and push the Docker image to Docker Hub:
   ```bash
   docker build -t <your-dockerhub-username>/db-demo-app:v1 .
   docker push <your-dockerhub-username>/db-demo-app:v1
   ```

2. **Ensure Kubernetes Cluster is Set Up**  
   Verify that your Kubernetes cluster is running and `kubectl` is configured:
   ```bash
   kubectl cluster-info
   ```

3. **Set Up MongoDB Pod**  
   Apply the MongoDB deployment file:
   ```bash
   kubectl apply -f deployment-service-mongodb.yaml
   ```

4. **Apply Mongo ConfigMap**  
   Apply the `mongo-config.yaml` file:
   ```bash
   kubectl apply -f mongo-config.yaml
   ```

5. **Update the Image in Deployment File**  
   Edit `deployment-service-db-demo-app.yaml` and update the `image` field to:
   ```
   image: <your-dockerhub-username>/db-demo-app:v1
   ```

6. **Deploy the Application**  
   Apply the updated deployment file:
   ```bash
   kubectl apply -f deployment-service-db-demo-app.yaml
   ```

7. **Run Persistent Volume Configuration**  
   Apply the `host-pv.yaml` file:
   ```bash
   kubectl apply -f host-pv.yaml
   ```

8. **Apply Persistent Volume Claim**  
   Apply the `host-pvc.yaml` file:
   ```bash
   kubectl apply -f host-pvc.yaml
   ```

9. **Access the Application**  
   Use Minikube to access the service:
   ```bash
   minikube service db-demo-app-service
   ```

## Notes

- Replace `<your-dockerhub-username>` with your Docker Hub username.
- Ensure all required Kubernetes configuration files are present in the repository.