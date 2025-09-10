# Java Maven EKS App

## Overview
This project is a Java application built using Maven, designed to be deployed on AWS EKS (Elastic Kubernetes Service) using ArgoCD for continuous deployment. The application includes a main class and corresponding unit tests.

## Project Structure
```
java-maven-eks-app
├── src
│   ├── main
│   │   └── java
│   │       └── App.java
│   └── test
│       └── java
│           └── AppTest.java
├── .github
│   └── workflows
│       └── ci-cd.yml
├── pom.xml
├── README.md
└── k8s
    └── deployment.yaml
```

## Prerequisites
- Java JDK 11 or higher
- Maven 3.6 or higher
- Docker
- AWS CLI configured with appropriate permissions
- ArgoCD installed on your Kubernetes cluster

## Setup Instructions
1. **Clone the repository:**
   ```bash
   git clone <repository-url>
   cd java-maven-eks-app
   ```

2. **Build the application:**
   Use Maven to compile the application:
   ```bash
   mvn clean install
   ```

3. **Run tests:**
   Execute the unit tests to ensure everything is working correctly:
   ```bash
   mvn test
   ```

4. **SonarQube Analysis:**
   Ensure you have SonarQube set up and configured. You can run the analysis using:
   ```bash
   mvn sonar:sonar
   ```

5. **Deploy to AWS EKS:**
   Ensure your `k8s/deployment.yaml` is configured correctly for your application. Use ArgoCD to deploy the application:
   ```bash
   argocd app create <app-name> --repo <repository-url> --path k8s --dest-server https://kubernetes.default.svc --dest-namespace <namespace>
   argocd app sync <app-name>
   ```

## Usage
After deployment, you can access the application via the service exposed in your Kubernetes cluster. Ensure to check the service type (LoadBalancer/NodePort) in your `deployment.yaml`.

## License
This project is licensed under the MIT License. See the LICENSE file for more details.