   
   ### ENTRYPOINT
   ENTRYPOINT is used to run a container just like CMD. But there are few differences...

1. We can't override entrypoint, but we can override CMD.

2. We can't override entrypoint, if you try to do so it will go and append to the ENTRYPOINT coomand.

3. If you use CMD and entrypoint and don't give any command from terminal, CMD acts as an argument provider   
   to  ENTRYPOINT.

4. CMD will supply default arguments to ENTRYPOINT.

5. You can always override CMD arguments from runtime

6. you can stop misusing your image with other commands


############################  Another response from ChatGPT: ENTRYPOINT ##############################

ENTRYPOINT and CMD are two instructions in Dockerfiles that are used to define how the container should behave when it is run.

ENTRYPOINT is a Dockerfile instruction that specifies the command that should be executed when the container is started. It is the primary command that runs in the container. The ENTRYPOINT can be defined as an array of strings or a single string. When defining the ENTRYPOINT, you must specify the full path to the executable or script that you want to run inside the container.

CMD, on the other hand, is used to provide default arguments for the ENTRYPOINT or to specify a command to be run if no ENTRYPOINT is specified. The CMD instruction is not mandatory in a Dockerfile, but if it is included, it must be placed after the ENTRYPOINT. You can also define CMD as an array of strings or a single string.

Here is an example of how ENTRYPOINT and CMD can be used together in a Dockerfile:

FROM alpine

ENTRYPOINT ["/bin/sh", "-c"]
CMD ["echo", "Hello, World!"]



In this example, the ENTRYPOINT is set to /bin/sh -c, which means that any additional commands specified in CMD will be passed to /bin/sh -c. The CMD is set to ["echo", "Hello, World!"], which means that if no command is specified when running the container, it will execute the echo command with the argument Hello, World!.

In summary, ENTRYPOINT is the primary command to be executed in the container, while CMD is used to provide default arguments for the ENTRYPOINT or to specify a command to be run if no ENTRYPOINT is specified.