# How to use Docker within git_image

This Dockerfile will create a docker image based off the latest Ubuntu image and will install git and ssh on it. 
```
FROM ubuntu

LABEL name="GIT"

RUN apt-get update -y
RUN apt-get install -y openssh-server
RUN apt-get install -y git

CMD ["/bin/bash"]
```

1. Create a volume for this image called git volume 
```
docker volume create git-volume
```

2. Create an image based off this Dockerfile with the following command.
```
$ docker build -t git .
```

3. Start the git_image container
```
$ docker run -it  --name GIT -v git-volume:/test_folder git
```

4. Configure git settings for your git account utilizing git config.
```
$ git config --global user.email "you@example.com"
$ git config --global user.name "Your Name"
```

5. Generate an SSH key for this container with your option of choice I suggest using keygen
```
$ ssh-keygen -t rsa -b 4096 -C "youremail"
# Enter a passphrase you would like to use
```

6. Copy the contents of your public that was generated to your clipboard andd add it to your Github SSH keys listed under your accounts. Go to github.com/settings/profile.

7. Now change directories to test_folder.
```
$ touch docker_git_test.txt
$ git add . 
$ git commit -m "Init commit"
$ git remote add origin (url to repo)
$ git branch -M main
$ git push -u origin main
```