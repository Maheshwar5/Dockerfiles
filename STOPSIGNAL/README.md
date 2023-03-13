### STOPSIGNAL

STOPSIGNAL is used how to exit the container.
* By default docker request for exit and wait for sometime.
* If it is not exiting you can force kill.
* When your container receives STOPSIGNAL, your application can perform
      * You can Close DB connections.
      * You can do some backup.



> When you run docker stop, you are instructing the Docker daemon to send a signal 
  to the process running the container to stop.

  By default, it does this by sending a SIGTERM and then wait a short period so the process can exit gracefully. If the process does not terminate within a grace period (10s by default, customisable), 
  it will send a SIGKILL.     