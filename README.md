# ShopSphere — Cloud-Native E-commerce Platform

ShopSphere is a full-stack e-commerce application built with React, Spring Boot, and PostgreSQL. This project focuses on implementing an end-to-end DevOps workflow using Microsoft Azure, Azure DevOps, Docker, and Kubernetes.

The objective is to build, deploy, secure, and monitor a containerized application while gaining practical experience with cloud infrastructure, CI/CD automation, Kubernetes orchestration, and production-oriented DevOps practices.

## Technology Stack

| Category | Technology |
|---|---|
| Frontend | React, Vite, JavaScript |
| Backend | Java 21, Spring Boot, Maven |
| Database | PostgreSQL |
| Containerization | Docker |
| Container Registry | Azure Container Registry (ACR) |
| Orchestration | Azure Kubernetes Service (AKS) |
| CI/CD | Azure DevOps YAML Pipelines |
| Secrets Management | Azure Key Vault, Managed Identities |
| Networking | Azure Virtual Network, Private Endpoints, Application Gateway |
| Monitoring | Azure Monitor, Application Insights, Container Logs |

## Architecture

The planned architecture separates application delivery, runtime infrastructure, and supporting cloud services.

```text
Developer
   |
   v
Azure DevOps Git Repository
   |
   v
Azure DevOps YAML Pipelines
   |
   +--> Build and Test Frontend
   |
   +--> Build and Test Backend
   |
   v
Docker Image Build
   |
   v
Azure Container Registry
   |
   v
Azure Kubernetes Service (AKS)
   |
   +--> Frontend Workloads
   |
   +--> Backend Workloads
              |
              v
       Azure Database for PostgreSQL

Supporting Services:
- Azure Key Vault
- Azure Managed Identities
- Azure Application Gateway
- Azure Monitor
```

The final architecture and network paths will be documented after the infrastructure is implemented and tested.

## Key Project Objectives

### 1. Containerization
- Create separate Docker images for the frontend and backend.
- Use appropriate image tagging and container configuration.
- Test containers locally before deploying to Azure.

### 2. CI/CD Automation
- Build Azure DevOps YAML pipelines for frontend and backend changes.
- Configure branch and path-based triggers.
- Run automated build and test steps.
- Publish versioned Docker images to Azure Container Registry.
- Deploy application updates to AKS and verify rollout status.

### 3. Kubernetes Orchestration
- Deploy application workloads using Kubernetes YAML manifests.
- Configure Deployments, Services, ConfigMaps, and ingress/routing where appropriate.
- Implement readiness and liveness probes.
- Configure resource requests and limits.
- Explore scaling and rolling updates.

### 4. Security and Networking
- Apply least-privilege access to Azure resources.
- Use managed identities and federated authentication where supported.
- Store application secrets in Azure Key Vault.
- Configure private connectivity for supported services.
- Restrict public access according to the intended architecture.

### 5. Monitoring and Troubleshooting
- Inspect Kubernetes pod status and application logs.
- Verify deployment health and application endpoints.
- Configure Azure monitoring and useful alerts.
- Document common failures and recovery procedures.

## Planned Repository Structure

```text
shopsphere-azure-devops/
├── frontend/
├── backend/
├── k8s/
├── pipelines/
├── docs/
├── azure-pipelines.yml
├── .gitignore
└── README.md
```

The repository structure may evolve as the implementation progresses.

## Project Status

**Current phase:** Azure DevOps CI/CD and AKS deployment preparation. Review `DEPLOYMENT-NOTES.md` before the first deployment.

The application source code is being prepared for containerization. Docker configuration, Kubernetes manifests, Azure infrastructure, Azure DevOps pipelines, private networking, and monitoring will be added and validated incrementally.

Features and infrastructure will be marked as completed only after implementation and verification.

## Security Practices

- Never commit passwords, tokens, private keys, or production secrets.
- Keep local environment files out of version control.
- Provide sanitized `.env.example` files when configuration documentation is needed.
- Use managed identities and appropriately scoped permissions where supported.
- Use unique image tags and validate deployments before release.
- Document network access and security decisions.

## Learning Outcomes

This project is intended to demonstrate practical experience with:

- Docker image creation and container troubleshooting
- Azure DevOps YAML pipelines and automated deployments
- Azure Container Registry and AKS
- Kubernetes manifests, health probes, and rollout strategies
- Azure networking and private connectivity
- Identity, access management, and secrets handling
- Monitoring, troubleshooting, and deployment verification

## Disclaimer

This is a portfolio and learning project. Production readiness depends on the implementation and verification of security, availability, disaster recovery, monitoring, and operational requirements.