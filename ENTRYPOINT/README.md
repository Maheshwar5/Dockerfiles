### ENTRYPOINT
ENTRYPOINT is used to run a container just like CMD. But there are few differences...

1. We can't override entrypoint, but we can override CMD.

2. We can't override entrypoint, if you try to do so it will go and append to the ENTRYPOINT coomand.


