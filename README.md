# cicdinfra: a CI/CD mockup with Jenkins2/Ansible/Docker


## Design

### Constraints

- Jenkins2
- Docker, Ansible

### Choices

- Make everything run on my personnal laptop, without installing
things system-wide
- Everything (including the infrastructure) in Docker
- As Jenkins will be powerfull on my laptop, no push notifications
from Github
- Push the concept of immutability: no app deployment via ansible,
only container deployments
- Separate infrastructure deployment (cicdinfra) and application (demo) deployment
- Use of Declarative Pipeline (vs Scripted) in Jenkins. Because it is recommended. Even if its not yet widely used.
- Use Ansible to reduce the DSL in Jenkins Pipeline.
- Blue/Green App deployment, or Rolling Update

### Infrastructure

- My Laptop: Docker Host, Docker client, Docker-Compose, and Ansible (for testing)
- Jenkins Container: Jenkins2, Docker-Compose, Docker client, Ansible
- LB Container: Nginx

## Pre-Requists
- Docker, Docker-Compose, ideally runned as non root-user

## Launch the infrastructure

- build the Jenkins image with Docker and Ansible (not found one suitable)
```
docker build -t 'lsioctl/jenkins-docker-ansible' -f Dockerfile-Jenkins .
```

- build the Nginx image with Python (for ansible)
```
docker build -t 'lsioctl/nginx' -f Dockerfile-Nginx .
```


- Launch Jenkins and the LB with docker-compose
```
docker-compose up
```

- For one type of deployment (Rolling Update), we will use Swarm mode
```
docker swarm init
```
