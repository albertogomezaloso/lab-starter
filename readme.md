```mermaid
sequenceDiagram
    participant GitRepo
    participant Jenkins
    participant Maven
    participant Docker
    participant Nexus
    participant Kubernetes
    participant Postman
    GitRepo ->> Jenkins: Checkout
    Jenkins ->> Maven: Build
    Maven ->> Maven: Test
    Maven ->> Maven: Package
    Maven ->> Nexus: Deploy to Nexus
    Jenkins ->> Docker: Build Docker Image
    Docker ->> Docker: Tag Docker Image
    Docker ->> Docker Hub: Authenticate to Docker Hub
    Docker Hub ->> Docker: Authenticate
    Docker ->> Docker Hub: Push Docker Image
    Jenkins ->> Kubernetes: Deploy to Staging
    Kubernetes ->> Kubernetes: Create Namespace
    Kubernetes ->> Kubernetes: Apply Deployment
    Kubernetes ->> Kubernetes: Apply Service
    Jenkins ->> Postman: Test Staging Deployment
    Jenkins ->> Kubernetes: Deploy to UAT
    Kubernetes ->> Kubernetes: Create Namespace
    Kubernetes ->> Kubernetes: Apply Deployment
    Kubernetes ->> Kubernetes: Apply Service
    Jenkins ->> Postman: Test UAT Deployment
    Jenkins ->> Kubernetes: Deploy to Production
    Kubernetes ->> Kubernetes: Create Namespace
    Kubernetes ->> Kubernetes: Apply Deployment
    Kubernetes ->> Kubernetes: Apply Service
    Jenkins ->> Postman: Test Production Deployment
  ```
