# Installing Jenkins on a Container


❯ sudo docker exec jenkins-blueocean cat /var/jenkins_home/secrets/initialAdminPassword

## Troubleshooting 
If you're using an M1 Mac remember to change the architecture of the debian system. 
The official jenkins tutorial assumes a amd64 architecture. 
```
"deb [arch=arm64] https://download.docker.com/linux/debian \
$(lsb_release -cs) stable"
```