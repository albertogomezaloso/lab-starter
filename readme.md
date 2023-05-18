```mermaid
sequenceDiagram
    participant Jenkins
    participant GitHub
    participant Nexus
    participant Docker
    participant Kubernetes
    participant Postman

    Jenkins->>GitHub: Checkout GitHub
    Jenkins->>Jenkins: Compile Maven
    Jenkins->>Jenkins: Test Maven
    Jenkins->>Jenkins: Package Maven
    Jenkins->>Nexus: Upload to Nexus
    Jenkins->>Docker: Build Docker Image
    Jenkins->>Docker: Push Docker Image
    Jenkins->>Kubernetes: Deploy to Staging Kubernetes
    Jenkins->>Postman: Validate Staging Postman
    Jenkins->>Kubernetes: Deploy to UAT Kubernetes
    Jenkins->>Postman: Validate UAT Postman
    Jenkins->>Kubernetes: Deploy to Production Kubernetes
    Jenkins->>Postman: Validate Production Postman
  ```
