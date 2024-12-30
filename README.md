# From Path to Pod, Efficient Routing with Ingress Load Balancer

## Project Description:
This project demonstrates the implementation of path-based routing using an AWS Application Load Balancer (ALB) integrated with Kubernetes Ingress, Services, and a Kubernetes cluster. The setup enables efficient traffic distribution to specific backend services Through (ALB) DNS or DNS name based on request paths (/happy, /sad, /angry), providing a scalable and organized solution for managing microservices in a cloud-native environment.

## Features:
1. Path-Based Routing: Routes traffic based on URL paths (e.g., /happy, /sad, /angry) to specific Kubernetes services.
2. Integration with AWS ALB: AWS ALB for high availability, scalability, and efficient load balancing.
3. Microservice Architecture: Each path corresponds to a separate microservice, promoting modular design.

## Workflow:
1. Kubernetes Cluster Setup: A Kubernetes cluster is provisioned to host containerized applications. The cluster acts as the foundation for managing workloads and services.
2. HTML code: through html code happy, sad, angry emojis have been created in .html file and according to that runtime and dependencies will written in deployment file
3. Service and Pod Deployment: Kubernetes Services expose backend pods for each path (happy-service, sad-service, angry-service).
Each service corresponds to a unique deployment managing one or more pods.
4.AWS ALB Creation: The AWS ALB is created and managed by ingress ,the AWS Load Balancer Controller, which integrates with Kubernetes Ingress resources.
Path-Based Routing Configuration: An Ingress resource is defined in the Kubernetes cluster with rules to route traffic based on URL paths (/happy, /sad, /angry).
The ingress uses the ALB to route incoming traffic to specific backend services.
5. Traffic Flow:1. Client Request: Traffic is directed to the AWS ALB, which forwards requests to the Kubernetes Ingress.
                              2. Ingress Processing: The Ingress resource evaluates the request path and routes it to the appropriate service.
                              3.  Service Delivery: The service sends the request to the matching pod, where the desired application logic is executed.

