# Spring Boot CI/CD Pipeline on AWS

## Project Overview

This project implements an automated CI/CD pipeline for deploying a containerized Spring Boot Inventory Management System on Amazon Web Services (AWS).

The solution automates the process from source-code changes through application build, Docker containerization, Amazon ECR image storage, and deployment to Amazon ECS.

## Architecture

GitHub → AWS CodePipeline → AWS CodeBuild → Docker → Amazon ECR → Amazon ECS → Spring Boot Application

## AWS Services Used

* GitHub – Source code repository
* AWS CodePipeline – CI/CD orchestration
* AWS CodeBuild – Application build and Docker image creation
* Amazon ECR – Docker container image repository
* Amazon ECS – Container deployment and hosting
* Amazon S3 – CodePipeline artifact storage
* AWS IAM – Access control and service permissions

## Application

The application is a Spring Boot Inventory Management System.

ECS Cluster:
`springboot-cluster`

ECS Service:
`springboot-service`

ECR Repository:
`springboot-cicd`

Container:
`springboot-container`

AWS Region:
`us-east-1`

## CI/CD Process

1. A developer commits a change to the GitHub `main` branch.
2. AWS CodePipeline automatically detects the change.
3. CodePipeline retrieves the source code.
4. AWS CodeBuild builds the Spring Boot application.
5. Docker creates a container image.
6. The image is pushed to Amazon ECR.
7. CodeBuild generates `imagedefinitions.json` for the ECS deployment.
8. AWS CodePipeline deploys the updated container to Amazon ECS.
9. ECS starts the updated application container.

## Build Configuration

The project uses `buildspec.yml` to define the CodeBuild process, including:

* Spring Boot application build
* Docker image creation
* Amazon ECR authentication
* Docker image push
* Generation of `imagedefinitions.json`

## Deployment Validation

The CI/CD pipeline was tested by committing an application change to the GitHub `main` branch.

The updated application was automatically built and deployed to Amazon ECS.

The successful deployment was validated through the live application, which displayed:

**Spring Boot Inventory Management System is running successfully! - CI/CD TEST v2**

## Project Outcome

The project demonstrates an automated CI/CD workflow that reduces manual deployment activities by integrating source control, automated builds, containerization, image management and ECS deployment.
