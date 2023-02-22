[![CircleCI](https://dl.circleci.com/status-badge/img/gh/Steve-ndeke/DevOps_Microservices/tree/main.svg?style=svg)](https://dl.circleci.com/status-badge/redirect/gh/Steve-ndeke/DevOps_Microservices/tree/main)

## Project Overview

In this project, you will apply the skills you have acquired in this course to operationalize a Machine Learning Microservice API.

You are given a pre-trained, `sklearn` model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on. You can read more about the data, which was initially taken from Kaggle, on [the data source site](https://www.kaggle.com/c/boston-housing). This project tests your ability to operationalize a Python flask app—in a provided file, `app.py`—that serves out predictions (inference) about housing prices through API calls. This project could be extended to any pre-trained machine learning model, such as those for image recognition and data labeling.

### Project Tasks

Your project goal is to operationalize this working, machine learning microservice using [kubernetes](https://kubernetes.io/), which is an open-source system for automating the management of containerized applications. In this project you will:

- Test your project code using linting
- Complete a Dockerfile to containerize this application
- Deploy your containerized application using Docker and make a prediction
- Improve the log statements in the source code for this application
- Configure Kubernetes and create a Kubernetes cluster
- Deploy a container using Kubernetes and make a prediction
- Upload a complete Github repo with CircleCI to indicate that your code has been tested

You can find a detailed [project rubric, here](https://review.udacity.com/#!/rubrics/2576/view).

**The final implementation of the project will showcase your abilities to operationalize production microservices.**

---

## Setup the Environment

Create a virtualenv and activate it Due to python3.7 are no longer availble in the installation packages, I used conda to create virtual enrinmrenet because I can still install python3.7 with conda. I have miniconda3 installed on my local computer
1.Run source ~/miniconda3/bin/activate to activate conda
2.Run conda create -n .devops python=3.7 to create virtual env with python3.7 installed
3.Run conda activate .devops to activate venv .devops
4.Run make install to install the necessary dependencies
5.Run make lint (pylint app.py files and hadolint Dockerfile) to detect errors in the code.
6.can also run make all instead of previous two steps.

### Running `app.py`

1. Standalone: `python app.py`
2. Run in Docker: `./run_docker.sh`
3. Run in Kubernetes: `./run_kubernetes.sh`

### Kubernetes Steps
Setup and Configure Docker locally
	1.install docker as described in the link.
	2.Run ./run_docker.sh
	3.Run docker ps to check if docker is running.
	4.Run ./make_prediction.sh to make prediction and copy/paste the logging info at terminal to output_txt_files/docker_out.txt

Setup and Configure Kubernetes locally
	1.Run curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
	2.Run sudo install minikube-linux-amd64 /usr/local/bin/minikube
	3.Run minikube start to start minikube
	4.Run kubectl get pods to see which pods are running.
	5.Run ./run_kubernetes.sh
	6.Run ./make_prediction.sh to make prediction and copy/paste the logging info at terminal to output_txt_files/kubernetes_out.txt
Create Flask app in Container
	1.Run ./run_docker.sh to build and start the Flask app container.
	2.Run ./upload_docker.sh to upload the container to docker hub.

###file changes
1.app.py Contains the code to handle the prediction. An extra log was added.
2.Dockerfile Holds the instructions on how to create docker image.
3.run_docker.sh Runs the application using docker.
4.upload_docker.sh Script that builds, tags and uploads the docker image to docker hub.
5.run_kubernetes.sh Runs deployed docker image using kubernetes.
6.output_txt_files/docker_out.txt Output logs from the docker execution.
7.output_txt_files/kubernetes_out.txt Output logs from the kubernetes execution.
