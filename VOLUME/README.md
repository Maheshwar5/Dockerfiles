Docker Volumes:


- Docker containers are Ephemeral.
- When you remove container by default it will delete the data.


- To make the data persist even after container termination, you need 
  Docker Volumes.

- Container Doesn't not have any Filesystem, it uses Hosts Filesystem.
  Docker Does't have any default Filesystem by it self.


- When container is terminated the Filesystem also get deleted, but using
  Docker Volumes we can persist the data even after container termination.
  Irrespective of container state the data will be available.



Scenario:

Docker stores information is...
/var/lib/docker/

This is where docker saves the full information.

In this there is overlay.

$ cd overlay2/

$ ls -l

Here, it'll create one random ID and then it will store the information for you.



Checking, where the container is storing data
----------------------------------------------

$ docker ps

containerID
-----------

$ docker inspect containerID

It'll show you where the data is storing 

"workdir": "/var/lib/docker/overlay2/xxxxxxxxxxxxxxx/work"


$ cd var/lib/docker/overlay2/xxxxxxxxxxxxxxx/work

$ ls -l

diff
link
lower
merged
work


$ cd diff/

It will store in some random directories. This is the place it stores data in Ephemeral.




Docker Volumes: /var/lib/docker/volumes
---------------------------------------

If you create a docker volume, there will be a directory called /var/lib/docker/volumes

Here it will create volume.

Command called volume create <name of the volume>

$ docker volume create nginx 

$ docker volume ls

$ docker volume inspect nginx

"Mountpoint": "/var/lib/docker/volumes/nginx/_data",

This is where it is created!




- How to attach the Volumes to the container:
  ------------------------------------------

Syntax:
$ docker run -d -v <volumename>: /<directoryname> -p 80:80 <imagename>

Like: -p host-port:container-port
      -v host-path:container-path



Practical:

$ docker run -d -v nginx:/usr/share/nginx/html -p 80:80 nginx

$ docker ps
containerID

$ sudo su -

$ cd /var/lib/docker/volumes/nginx/_data/

$ ls -l



Just create a file to do volume test:

$ echo "Hello World!" > hi.html

Test it in the browser: <publicIP/hi.html>


Exit from conatiner...

Now, remove the container and test:

$ docker ps

$ docker rm -f containerID

Checking if the file exists:

$ sudo su -
$ cd /var/lib/docker/volumes/nginx/_data/
$ ls -l

You find the created file!


If you create the container again, the data persists.



Container data is ephemeral it always refer to the Host server Filesystem,
by default when you terminate the container, the data gets deleted.

But,

If you create Docker Volume and mount it to container the data will not be deleted
by default. Data persists and you can again provide the same path to new containers 
and you can still access the data.




Anonymous Volumes:
-----------------

# Instead of Creating Volume,

    Creaing a Directory & host it. You can do this method also...

$ pwd
$ mkdir test-data

Creating a new container to use test-data directory.
$ docker run -d -v /home/ect-user/test-data:/usr/share/nginx/html -p 8080:80 nginx


$ docker ps

$ cd test-data/

$ echo "hello" > hi.html

open browser, browse...<IP:8080/hi.html>

There are multiple ways of creating Docker Volumes, 


You can directly give like above. This is type of creating Volumes i known as Anonymous Volumes.

Anonymous Volumes are not managed by Docker. 

If you check, it will not show the volumes...

$ docker volume ls

Because you created it manually, and not used Docker command to create it. Hence it is called Anonymous Volume.



Another way by using Docker Command:
-----------------------------------
If you create the Volume with Docker command, Docker will manage that Volume.
Then it becomes Docker Volumes.

This is the best recommendation to create Docker Volumes using Docker Command.



