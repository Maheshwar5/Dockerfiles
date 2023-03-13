FROM almalinux
RUN yum install nginx -y
# when image creator is running this below command willl not run. When someone else tries to use your image then it will run. 
ONBUILD ADD simple.txt /tmp/  
ONBUILD RUN 