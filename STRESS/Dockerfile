# This is used to apply some stress on the containers 
FROM almalinux:8
RUN yum update -yum
RUN yum install stres-ng -y
CMD ["stress-ng", "--help"] # to test the resources
