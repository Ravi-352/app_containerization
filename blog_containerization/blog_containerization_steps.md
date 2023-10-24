PART-1: CREATING DOCKER IMAGE AND PUSHING IT TO DOCKER HUB

Clone the git repo of the nodejs app - https://github.com/Ravi-352/app_containerization.git

 cd blog_containerization

You should be able to see following file structure - 



Dockerfile helps in assembling the docker image for creating container in which the nodejs app will run

Command to create docker image: 
sudo docker build -t <dockerhub repo path where image needs to be stored:tag> .


For this demo, docker hub repo path is - 

So the command to create docker image can be - 
sudo docker build -t ravi352/rk_personal_apps:myblog_demo.1.0.0 .

After the image gets created, we can search for the image in the local machine using following command - 



Now we can run the docker image to create the container - 
sudo docker run --name myblog_demo1 -p 3000:8080 -d ravi352/rk_personal_apps:myblog_demo.1.0.0



Now try accessing "localhost:3000" from any of the web browsers



Now that the app is tested in local and working fine, we can kill the container using following command:
Docker stop <container id>

Next step is to push the image to docker hub using following commands:
Sudo su -
docker login
Docker push <docker image>

In this case:
sudo docker push ravi352/rk_personal_apps:myblog_demo.1.0.0

Now verify in dockerhub by logging in -
 



Now that the image is available over dockerhub, we need to test if the image works fine in a remote server. For this we proceed to PART-2 of the project. 


PART-2: TESTING THE IMAGE IN REMOTE SERVER (AWS EC2 instance)

Create EC2 Instance - with ubuntu image




Connect from SSH - 




Log in to ubuntu ssh




Sudo su -
Apt-get update
Apt-get install git
Apt-get install nodejs
Apt-get install docker/ snap install docker
Docker run hello-world



docker pull ravi352/rk_personal_apps:myblog_demo.1.0.0
docker images 
 docker run --name myblog_demo1 -p 80:8080 -d ravi352/rk_personal_apps:myblog_demo.1.0.0

docker ps --format "table {{.Image}}\t{{.Ports}}\t{{.Names}}"




Accessing the app using public ip of ec2 instance with port 80 -







Now stop the container
Docker stop <container id>


Terminate the ec2 instance
![image](https://github.com/Ravi-352/app_containerization/assets/91112573/68bb65ef-37b0-4788-91e2-8d99cd65aa57)

