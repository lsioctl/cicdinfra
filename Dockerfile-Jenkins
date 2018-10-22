FROM jenkins/jenkins:lts
USER root
RUN apt-get update
RUN apt-get remove -y docker
RUN apt-get install -y software-properties-common \
apt-transport-https
RUN curl -fsSL https://download.docker.com/linux/debian/gpg | \
apt-key add -
RUN add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/debian \
   $(lsb_release -cs) \
   stable"
RUN apt-get update
RUN apt-get install -y docker-ce
RUN apt-get install -y python-pip
RUN pip install --upgrade pip
RUN pip install docker-compose
RUN pip install ansible
