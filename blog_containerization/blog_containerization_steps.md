![image](https://github.com/Ravi-352/app_containerization/assets/91112573/94a12836-b843-4159-89db-88ebdc26eadc)PART-1: CREATING DOCKER IMAGE AND PUSHING IT TO DOCKER HUB

Clone the git repo of the nodejs app - https://github.com/Ravi-352/app_containerization.git

```
cd blog_containerization
```
You should be able to see following file structure - 
![image](https://github.com/Ravi-352/app_containerization/assets/91112573/3b96350c-da66-433e-866a-824bafda7735)

Dockerfile helps in assembling the docker image for creating container in which the nodejs app will run

Command to create docker image: 

```
sudo docker build -t <dockerhub repo path where image needs to be stored:tag> .
```
For this demo, docker hub repo path is - 
![image](https://github.com/Ravi-352/app_containerization/assets/91112573/3d5e5e12-d3ff-4798-afb5-370794722e82)

So the command to create docker image can be - 
```
sudo docker build -t ravi352/rk_personal_apps:myblog_demo.1.0.0 .
```
After the image gets created, we can search for the image in the local machine using following command -
![image](https://github.com/Ravi-352/app_containerization/assets/91112573/62e0b570-22f8-481f-9661-ad9513f57fc5)

Now we can run the docker image to create the container - 
```
sudo docker run --name myblog_demo1 -p 3000:8080 -d ravi352/rk_personal_apps:myblog_demo.1.0.0
```

![image](https://github.com/Ravi-352/app_containerization/assets/91112573/1997b380-b24b-4866-a64d-56d6a39c4aff)

Now try accessing "localhost:3000" from any of the web browsers - 
![image](https://github.com/Ravi-352/app_containerization/assets/91112573/63ed9565-dc96-440f-81aa-0f83cb7fe61f)


Now that the app is tested in local and working fine, we can kill the container using following command:
```
Docker stop <container id>
```

Next step is to push the image to docker hub using following commands:

```
sudo su -
docker login
docker push <docker image>
#In this case -
sudo docker push ravi352/rk_personal_apps:myblog_demo.1.0.0

Now verify in dockerhub by logging in -
![image](https://github.com/Ravi-352/app_containerization/assets/91112573/cf87af98-7ab3-4502-8038-152b5cc28d27)

Now that the image is available over dockerhub, we need to test if the image works fine in a remote server. For this we proceed to PART-2 of the project.  
























