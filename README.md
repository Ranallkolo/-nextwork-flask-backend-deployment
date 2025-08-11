<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Deploy Backend with Kubernetes

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-compute-eks4)

**Author:** Abdulrahman Abdulkadir  
**Email:** abdabdulkadir62@gmail.com

---

## Deploy Backend with Kubernetes

![Image](http://learn.nextwork.org/confident_turquoise_quiet_hyena/uploads/aws-compute-eks4_6cfb382f2)

---

## Introducing Today's Project!

In this project, I will deploy the backend with Kubernetes because it provides automated deployment, scaling, and management of containerized applications, ensuring the backend is highly available, resilient, and easy to maintain.


### Tools and concepts

I used Kubernetes, ECR, kubectl, eksctl, and Docker to build, store, and deploy the backend application in an Amazon EKS cluster. Key concepts include using manifests to define deployments and services, containerizing applications for consistent execution, and leveraging Kubernetes orchestration to ensure scalability, high availability, and fault tolerance.


### Project reflection

This project took me approximately 1 hour and 30 minutes. The most challenging part was ensuring all AWS permissions and configurations were correctly set up for EKS and ECR access. My favourite part was seeing the backend pods running successfully and being able to access the service externally.


---

## Project Set Up

### Kubernetes cluster

To set up today's project, I launched a Kubernetes cluster. The cluster's role in this deployment is to orchestrate and manage the backend application's containers, ensuring they are deployed, scaled, and maintained across worker nodes while providing networking, load balancing, and high availability.


### Backend code

I retrieved backend code by cloning the repository from its remote source using Git. Pulling code is essential to this deployment because it provides the application files and configuration needed to build, containerize, and deploy the backend onto the Kubernetes cluster.


### Container image

Once I cloned the backend code, I built a container image because it bundles the application, dependencies, and runtime environment into a portable unit that can run consistently anywhere. Without an image, it would be difficult for Kubernetes to deploy, scale, and manage the backend reliably across different nodes.


I also pushed the container image to a container registry, which is Amazon ECR, to store and manage the image securely in a location accessible to my Kubernetes cluster. ECR facilitates scaling for my deployment because it allows multiple cluster nodes to pull the same image quickly and reliably when creating or scaling backend pods.


---

## Manifest files

Kubernetes manifests are YAML or JSON configuration files that define the desired state of Kubernetes resources, such as deployments, services, and volumes. Manifests are helpful because they allow you to declaratively manage your application setup, making deployments repeatable, consistent, and easy to update or roll back.


A Deployment manifest manages how many replicas of a pod should run, how updates are rolled out, and how containers are configured within those pods. The container image URL in my Deployment manifest tells Kubernetes which container image to pull and run for the backend application.


A Service resource exposes a set of pods as a network service, allowing them to be accessed consistently even if individual pods are replaced or rescheduled. My Service manifest sets up a NodePort service that maps port 8080 on the pods to a port on each cluster node, enabling external access to the backend application.


![Image](http://learn.nextwork.org/confident_turquoise_quiet_hyena/uploads/aws-compute-eks4_b01876554)

---

## Backend Deployment!

To deploy my backend application, I used kubectl to apply the deployment and service manifests, which created the necessary pods and exposed them through a NodePort so the application could be accessed externally.


### kubectl

kubectl is a command-line tool used to interact with Kubernetes clusters by creating, updating, and managing resources. I need this tool to apply manifests, check pod statuses, and troubleshoot deployments. I can't use eksctl for the job because eksctl is mainly for creating and managing the EKS cluster itself, not for deploying and controlling applications inside the cluster.


![Image](http://learn.nextwork.org/confident_turquoise_quiet_hyena/uploads/aws-compute-eks4_6cfb382f2)

---

## Verifying Deployment

My extension for this project is to use the EKS console to visually inspect cluster resources, check pod statuses, and troubleshoot any deployment issues. I had to set up IAM access policies because the EKS console requires explicit permissions to view and manage cluster resources. I set up access by attaching an IAM policy to my user or role using its IAM ARN, granting the necessary EKS permissions.


Once I gained access into my cluster's nodes, I discovered pods running inside each node. Pods are the smallest deployable units in Kubernetes, containing one or more tightly coupled containers that share the same network namespace and storage volumes. Containers in a pod share the same IP address, ports, and can communicate with each other over localhost.


The EKS console shows you the events for each pod, where I could see logs of scheduling, container image pulling, and container startup activities. This validated that the backend pod was created successfully, the image was pulled from ECR without errors, and the application container started running as expected.


![Image](http://learn.nextwork.org/confident_turquoise_quiet_hyena/uploads/aws-compute-eks4_3b391f873)

---

---
