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
```
## Running on Kubernetes with Minikube

### Start Minikube

```bash
minikube start
```
Deploy the application
```bash
kubectl apply -f k8s/ecommerce-all.yaml
```
Verify resources
```bash
kubectl get all -n ecommerce
```
Access the application
```bash
kubectl port-forward -n ecommerce svc/nginx-gateway 8080:80
```
##Then open:
```bash
http://localhost:8080
```

##Testing the APIs
##est through the gateway
```bash
curl -i http://localhost:8080/products/
```
```bash
curl -i http://localhost:8080/orders/
```
```bash
curl -i http://localhost:8080/users/
```
```bash
curl -i http://localhost:8080/payments/
```

##Port-forward directly to a microservice for manual testing
```bash
kubectl port-forward -n ecommerce svc/products-service 8081:8081
```
##########Example direct test to products-service#################
```bash
curl -i http://localhost:8081/products/
```
