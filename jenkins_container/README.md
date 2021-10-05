# Installing Jenkins on a Container

## Steps to replicate

1. Follow this [tutorial](https://www.jenkins.io/doc/tutorials/create-a-pipeline-in-blue-ocean/)

2. Once you're at the jenkins setup use the following command to find the initial admin password for jenkins setup.
```
sudo docker exec jenkins-blueocean cat /var/jenkins_home/secrets/initialAdminPassword
```

## Troubleshooting 
If you're using an M1 Mac remember to change the architecture of the debian system. 
The official jenkins tutorial assumes a amd64 architecture. 
```
"deb [arch=arm64] https://download.docker.com/linux/debian \
$(lsb_release -cs) stable"
```