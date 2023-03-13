### ARG

ARG is used to supply few variables at the image creation.
* ARG is the only instruction you can use before FROM.
ARG decalred before cannot be accessed after instruction. 

# Using ENV and ARG for best results.
* Create one env variable and assign the variable of ARG to that.
* Then we can access the ARG values through ENV both in image and container.