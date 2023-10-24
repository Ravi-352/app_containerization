**PART-2: TESTING THE IMAGE IN REMOTE SERVER (Free tier AWS EC2 instance)**

Create AWS EC2 instance - with "ubuntu" image

![image](https://github.com/Ravi-352/app_containerization/assets/91112573/debab22e-3d20-4fb2-8511-7b2a25aabaf0)

Connect from local terminal using the access key pem file. Create one from AWS console if not there already. In this case it was already created and 
the name give was 'tindog-demo.pem'.

![image](https://github.com/Ravi-352/app_containerization/assets/91112573/75e6b552-c62f-4bdd-8436-231b426a8d02)

![image](https://github.com/Ravi-352/app_containerization/assets/91112573/8d6fe14d-c97c-46c9-bc9a-91e83af2c2a5)

![image](https://github.com/Ravi-352/app_containerization/assets/91112573/60142edc-e26c-4bca-9538-3793602ae347)

![image](https://github.com/Ravi-352/app_containerization/assets/91112573/48a489b1-4658-468a-9945-ef5ee9cebd57)

Updating system files and installing git, nodejs and docker - 

```
sudo su -
apt-get update
apt-get install git
apt-get install nodejs
apt-get install docker/ snap install docker
docker run hello-world
```
Refer to the dockerhub docs - 
https://docs.docker.com/engine/install/ubuntu/ or 
https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04

Now check docker status and start if not started - 
```
systemctl status docker
sudo systemctl start docker
```
![image](https://github.com/Ravi-352/app_containerization/assets/91112573/42873a05-f124-436c-bf1d-9657ffe308bb)

Once docker is up, pull the required image from dockerhub - 

![image](https://github.com/Ravi-352/app_containerization/assets/91112573/4dcbcdc3-c6b3-4672-9d53-9df170ced960)


Now check if the image is pulled successfully - 
```
docker images
```

Now create the container for the image --
```
docker run --name myblog_demo1 -p 80:8080 -d ravi352/rk_personal_apps:myblog_demo.1.0.0
```

Check if the container is up and active - 
```
docker ps --format "table {{.Image}}\t{{.Ports}}\t{{.Names}}"
```

![image](https://github.com/Ravi-352/app_containerization/assets/91112573/211967cd-fcc2-434f-88ef-5427b9403e4b)

****Accessing the app using public ip of ec2 instance with port 80 -

![image](https://github.com/Ravi-352/app_containerization/assets/91112573/3bf13cdd-a622-437a-b6bf-e7f81810323c)

![image](https://github.com/Ravi-352/app_containerization/assets/91112573/7acc735e-1978-4c39-9dc6-8911b7694741)

```
#Now stop the container
Docker stop <container id>
```
To avoid unnecessary costing, terminate the EC2 Instance as soon the requirement is fulfilled as this is just for demo purpose.
















