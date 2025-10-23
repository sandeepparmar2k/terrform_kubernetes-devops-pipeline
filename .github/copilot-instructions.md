# AI Coding Agent Instructions for `terrform_kubernetes-devops-pipeline`

## Overview
This repository contains a DevOps pipeline setup for deploying microservices to Kubernetes clusters on AWS and Azure. It includes Terraform configurations, Kubernetes manifests, and CI/CD pipeline definitions. The project is structured to support two microservices:

1. **Currency Exchange Microservice**
2. **Currency Conversion Microservice**

## Key Components

### Microservices
- **Currency Exchange Microservice**
  - Located in `01-currency-exchange-microservice-basic/`
  - Contains a `Dockerfile` for containerization and a `pom.xml` for Maven-based Java builds.
  - Kubernetes deployment manifests are in `configuration/kubernetes/deployment.yaml`.

- **Currency Conversion Microservice**
  - Located in `02-currency-conversion-microservice-basic/`
  - Similar structure to the Currency Exchange Microservice.

### Infrastructure as Code (IaC)
- **Terraform Configurations**
  - AWS Kubernetes setup: `configuration/iaac/aws/kubernetes/main.tf`
  - Azure Kubernetes setup: `configuration/iaac/azure/kubernetes/main.tf`

### CI/CD Pipelines
- Azure Pipelines:
  - Found in `pipeline-backups/`.
  - Examples include `05-azure-kubernetes-cluster-iaac-pipeline.yml` and `06-azure-kubernetes-code-ci-cd-pipeline.yml`.
- AWS Pipelines:
  - Examples include `07-aws-kubernetes-cluster-iaac-pipeline.yml` and `08-aws-kubernetes-code-ci-cd-pipeline.yml`.

## Developer Workflows

### Building Microservices
- Use Maven to build the Java microservices:
  ```bash
  mvn clean install
  ```

### Running Tests
- Unit tests are located under `src/test/java/` for each microservice.
- Run tests with Maven:
  ```bash
  mvn test
  ```

### Deploying to Kubernetes
- Apply Kubernetes manifests using `kubectl`:
  ```bash
  kubectl apply -f <manifest-file>
  ```

### Terraform Workflows
- Initialize Terraform:
  ```bash
  terraform init
  ```
- Plan and apply changes:
  ```bash
  terraform plan
  terraform apply
  ```

## Project-Specific Conventions
- **Pipeline Backups**: YAML files in `pipeline-backups/` serve as templates or historical references for CI/CD pipelines.
- **Environment-Specific Configurations**: Separate Terraform configurations for AWS and Azure.
- **Kubernetes Manifests**: Organized under `configuration/kubernetes/`.

## Integration Points
- **External Dependencies**:
  - Kubernetes clusters on AWS and Azure.
  - Docker for containerization.
  - Maven for Java builds.
- **Cross-Component Communication**:
  - Microservices communicate via REST APIs.

## Examples
- Refer to `01-currency-exchange-microservice-basic/configuration/kubernetes/deployment.yaml` for a Kubernetes deployment example.
- Check `pipeline-backups/06-azure-kubernetes-code-ci-cd-pipeline.yml` for a CI/CD pipeline example.

---

Feel free to update this document as the project evolves.