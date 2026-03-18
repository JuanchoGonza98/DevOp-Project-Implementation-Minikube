# DevOp-Project-Implementation-Minikube
My own Ecommerce microservice architecture runs on minikube :)
# DevOps Microservices Ecommerce

A personal project focused on practicing **microservices architecture**, **containerization**, **Kubernetes**, and **DevOps workflows** through a simple ecommerce platform.

This project currently supports deployment in:

- **Docker Compose**
- **Kubernetes with Minikube**

The next stage of the project will be to provision cloud infrastructure in **AWS** using **Terraform** and deploy the platform on **Amazon EKS**.

---

## Project Overview

This repository was created as a hands-on lab to strengthen practical skills in:

- Microservices-based application design
- Containerization with Docker
- Service orchestration with Kubernetes
- Internal service-to-service communication
- Reverse proxy / API gateway patterns
- Infrastructure evolution from local environments to cloud platforms
- Future Infrastructure as Code practices with Terraform

The goal is not only to make the application work, but also to evolve it progressively toward a more production-oriented architecture.

---

## Current Architecture

The platform is composed of the following components:

- **frontend**: web interface for the ecommerce
- **nginx-gateway**: reverse proxy and single entry point
- **products-service**: manages products and stock
- **orders-service**: handles order creation and retrieval
- **payments-service**: processes payments
- **users-service**: manages users

### High-level flow

```text
Client / Browser
       |
       v
  nginx-gateway
       |
       +--> frontend
       +--> products-service
       +--> orders-service
       +--> payments-service
       +--> users-service

