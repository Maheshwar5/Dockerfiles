   
   ### ENTRYPOINT
   ENTRYPOINT is used to run a container just like CMD. But there are few differences...

1. We can't override entrypoint, but we can override CMD.

2. We can't override entrypoint, if you try to do so it will go and append to the ENTRYPOINT coomand.

3. If you use CMD and entrypoint and don't give any command from terminal, CMD acts as an argument provider   
   to  ENTRYPOINT.

4. CMD will supply default arguments to ENTRYPOINT.

5. You can always override CMD arguments from runtime

6. you can stop misusing your image with other commands