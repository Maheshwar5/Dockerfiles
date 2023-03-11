Docker Commands: 
Workout1: Docker Installation, Day 1

Initial step: update system: sudo yum update -y

Installing docker: 
sudo amazon-linux-extras install docker

To start and enable docker service: 
sudo service docker start
systemctl enable docker

Adding ec2-user to docker group: 
sudo usermod -a -G docker ec2-user
 

CMD to Display docker images:
docker images

To pull image from docker hub:
docker pull nginx


To create docker container:
docker create <ImageID>

To start docker container:
docker start 78629b683ecb

To list out containers:
docker ps

To list out all containers:
docker ps -a

To inspect a container:
docker inspect 78629b683ecb


To stop a container:
docker stop 78629b683ecb

To remove a container: First stop the container then remove.
docker rm <cotainerID>


To remove image:
docker rmi 904b8cb13b93


Docker run: pull + create + run  = Three in one command.
docker run nginx


To run container in detach mode:
docker run -d nginx


To run container in detach mode + assign a port:
docker run -d -p 80:80 nginx


To remove container forcefully:
docker remove -f <containerrID>

docker rm -f <containerrID>

To name a container:
docker run -d -p 80:80 --name nginx-container nginx



To interact with the container:
   docker exec -it <containerID> bash
   

Commands in interactive mode:

    7  cd /usr/share/nginx/html/
    8  ll
    9  ls -l



   10  echo "Hello Mahesh" > hi.html

       cd /usr/share/nginx/html



To Exit from container interactice mode:
ctrl + d