# Tutorial CI/CD with GitHub Action Lab

##  1. Intoduction

- Walkthrough DevSecOps Flow Overview
- [Azure Subscription](cloud-resources/subscription.md) & Access

##  2. Version Control

- Walkthrough Git & GitHub
- [Register GitHub & Create User](github/github-register.md)
- [Create Application Repository](github/create-repository.md)
    - [name]-tutorial-backend
    - [name]-tutorial-frontend
- Demo [Git Command](./github/git-command.md)

##  3. Application Design & Implementation

- [Initialize Project](apps/init-project-tutorial.md)
- Execute Unit test & Reports
    - [tutorial-backend](https://github.com/tarathep/tutorial-backend/blob/main/README.md#unit-test)
    - [tutorial-frontend](https://github.com/tarathep/tutorial-frontend/blob/main/README.md#unit-test)
- Run Application Stack
    - [tutorial-backend](https://github.com/tarathep/tutorial-backend/blob/main/README.md)
    - [tutorial-frontend](https://github.com/tarathep/tutorial-frontend/blob/main/README.md)

##  4. Containerization

- Walkthrough [Containerize with Docker](docker/Readme.md)
- [Docker File & Build Image](docker/create-dockerfile.md) 
- Image Registry on [DockerHub](https://hub.docker.com)
- Run all stack using [Docker Compose](docker/compose.md)

##  5. Azure Cloud Resources for CI/CD

- Walkthrough Azure Cloud Resources & Create
    - [Create Resource Group](cloud-resources/create-resource-group.md)
    - [Create App Service (Container)](cloud-resources/create-app-service-contaner.md)
    - [Create App Service (Code)](cloud-resources/create-app-service-code.md)
    - [Create Create Kubernetes Service (Optional)](cloud-resources/create-aks.md)
    - [Create Azure Container Registry](cloud-resources/create-acr.md)
    - [Create CosmosDB for MongoDB](cloud-resources/create-cosmos-mongodb.md)
- Deploy Apps to Web App

##  6. Container Orchestration

- Walkthrough Azure Kubernetes Service
- Demo Deployment Application with YAML files
- Demo Application stack on AKS

##  7. Helm Chart

- Create Chart with YAML files
- Deploy Application via Template

##  8. CI/CD GitHub Actions

- Walkthtough GitHub Action
- Create & Execute Component Workflows

##  9. [Continuous Integration](ci/Readme.md)

- Unittest
- SAST (Static Application Security Testing)
- Build (Arifact & Image)

##  10. [Continuous Deployment](cd/Readme.md)

- Deploy Application
- DAST (Dynamic Application Security Testing)
- Business Test with Automate Testing
- Review E2E Application & pipeline

