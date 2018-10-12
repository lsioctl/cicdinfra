# cicdinfra: a CI/CD mockup with Jenkins2/Ansible/Docker

## Design

### Constraints

- Jenkins2
- Docker, Ansible

### Choices

- make everything run on my personnal laptop, without installing
things system-wide
- everything (including the infrastructure) in Docker
- as Jenkins will be powerfull on my laptop, no push notifications
from Github
- push the concept of immutability: no app deployment via ansible,
only container deployments
- separate infrastructure deployment (cicdinfra) and application (demo) deployment
- Use of Declarative Pipeline (vs Scripted) in Jenkins. Because it is recommended. Even if its not yet widely used.
- Use Ansible to reduce the DSL in Jenkins Pipeline.
- Blue/Green App deployment

### Infrastructure

- My Laptop: Docker Host, Docker client, Docker-Compose, and Ansible (for testing)
- Jenkins Container: Jenkins2, Docker-Compose, Docker client, Ansible
- LB Container: Squid.
