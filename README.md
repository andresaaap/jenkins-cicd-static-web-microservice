## Intro

This is a Jenkins CI CI/CD pipeline for microservices, pushing Docker containers to the Docker repository and deploying them to a Kubernetes cluster in AWS EKS. This will create value by making the code building process and deploying faster and automatic.

## Install

To be able to use this CI/CD pipeline we will need:
- Jenkins
- eksctl
- aws cli
- docker
- kubectl

1. To install Jenkins please follow this guide http://jenkins.io/doc/book/installing/
2. To install docker please follow this guide https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-18-04
3. To install eksctl, aws cli and kubectl follow this guide https://docs.aws.amazon.com/eks/latest/userguide/getting-started-eksctl.html

## Project explanation

The pipeline has the following stages. First, there is a linting stage using the library **tidy** to **lint the HTML** and catch errors in the HTML. Please look at the image: lint.png

Then, I use **docker cli** to build the image and push it to a docker repository. Please look at the images: build-image.png push-image.png docker-image-repository.png

Then, there is a stage where I use **kubectl** to deploy the docker image to the cluster in the blue and green pod and create a **service** that redirects traffic to the blue pod. Please look at the images: deploy-blue-container.png deploy-green-container.png service-redirect-blue.png

Then, there is a stage where the **service** is updated to redirect traffic to the green pod. Please look at the image: service-redirect-green.png

Finally, the website can be access using the URL of the service and the port. Please look at the images: website.png service-pods.png

## Resources & Links

- [Great starting examples of CICD pipelines for kubernetes apps using CircleCI and AWS EKS
](https://andresaaap.medium.com/great-starting-examples-of-cicd-pipelines-for-kubernetes-apps-using-circleci-and-aws-eks-38985e3b3529)
- [Testing a container app or microservices app to deploy it to an AWS EKS cluster
](https://andresaaap.medium.com/testing-a-container-app-or-microservices-app-to-deploy-it-to-an-aws-eks-cluster-2b8778e22d21)
- [Errors in kubernetes and debugging](https://andresaaap.medium.com/errors-in-kubernetes-and-debugging-a7b803632bd9)
- [How to configure and execute a rolling update strategy in kubernetes?](https://andresaaap.medium.com/how-to-configure-and-execute-a-rolling-update-strategy-in-kubernetes-5e662be968b)
- [How to install docker, aws cli, eksctl, kubectl for Jenkins in Linux Ubuntu 18.04?](https://andresaaap.medium.com/how-to-install-docker-aws-cli-eksctl-kubectl-for-jenkins-in-linux-ubuntu-18-04-3e3c4ceeb71)
- [Simple blue-green deployment in kubernetes using minikube, Capstone project, Cloud DevOps Nanodegree](https://andresaaap.medium.com/simple-blue-green-deployment-in-kubernetes-using-minikube-b88907b2e267)
- [Capstone project, Cloud DevOps Nanodegree FAQ](https://andresaaap.medium.com/capstone-cloud-devops-nanodegree-4493ab439d48)

