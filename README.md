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
AWS ALB Creation: The AWS ALB is created and managed by ingress ,the AWS Load Balancer Controller, which integrates with Kubernetes Ingress resources.
4. Path-Based Routing Configuration: An Ingress resource is defined in the Kubernetes cluster with rules to route traffic based on URL paths (/happy, /sad, /angry).
The ingress uses the ALB to route incoming traffic to specific backend services.
5. Traffic Flow:1. Client Request: Traffic is directed to the AWS ALB, which forwards requests to the Kubernetes Ingress.
                              2. Ingress Processing: The Ingress resource evaluates the request path and routes it to the appropriate service.
                              3.  Service Delivery: The service sends the request to the matching pod, where the desired application logic is executed.

## Overview:

![Copy of Cloud Architecture - Page 1](https://github.com/user-attachments/assets/1333e0b8-4fbe-4aae-884e-9d10c6602302)

## Steps to do :
### Step 1 :     
### Create EC2 instance:

![image-1](https://github.com/user-attachments/assets/36dbb2ed-cf75-4acf-b6ed-13bb8787758c)

2. you can use Instance type as t2.medium or larger instance type than this because it is the requirement for kubernetes cluster
3. After that first you have to install Docker ,kubectl,eksctl,aws cli from their official website
   

![image-2](https://github.com/user-attachments/assets/187ddb5b-5fa1-46e1-afe7-ce4b5248a4fb)

### Step 2 :
4. Use the cluster.yml file to create cluster using eksctl command
   ```
   eksctl create cluster -f cluster.yml
   ```
6. Then Build Docker Image through Docker build and push those images in AWS ECR then use this image link in your deployment file
   ```
   docker build -t happy -f happy .       
   docker build -t sad -f sad .
   docker build -t angry -f angry .
   ```
   
![Screenshot 2024-12-31 235148](https://github.com/user-attachments/assets/1c6e342d-e03f-40ff-b9ae-827613bce45c)

### Step 3 :
6. Then execute the deployment.yml file through kubectl commands and service.yml file also where we have created cluster ip (within the cluster) so that we can see our webpage is running good
```
kubectl apply -f deployment.yml
kubectl apply -f service.yml
```
   
   
![image-3](https://github.com/user-attachments/assets/257e2313-78a8-4b64-a4ec-e4eafd031962)

### Step 4 :
7. Now we are ready to create our Ingress, for that first we need to create controller and all those commands are available on AWS official Documentation

![image-4](https://github.com/user-attachments/assets/ca8aa7e8-434f-413e-be8d-e3905af867aa)

8. After all steps has done succesfully you will see your controller is ready

![image-5](https://github.com/user-attachments/assets/50a6637d-fdee-4488-af91-210af9cbc425)
### Step 5 :
9. Now use my files ingress-resource.yml and ingressclass.yml file to create your load-balancer
```
kubectl apply -f ingress-resource.yml
kubectl apply -f ingressclass.yml
```
   
![image-6](https://github.com/user-attachments/assets/fd57c844-eaf5-4b0d-ad05-001b97eb676a)
![image-7](https://github.com/user-attachments/assets/33a27735-604d-4cf0-8551-b05a7607b443)
![image-8](https://github.com/user-attachments/assets/d43841b0-d930-4f8a-8127-70f9b75edb75)
![image-9](https://github.com/user-attachments/assets/b06bb188-05ff-44bc-b276-990f345cadb8)
![image-10](https://github.com/user-attachments/assets/a1c07f5e-e867-4566-894d-0f5341bd51a4)
