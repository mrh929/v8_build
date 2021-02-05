### What is This?

This is a docker that automatically compiles v8 source code and package it for download. You can submit it directly to [dockerhub](hub.docker.com) , and it will automatically fetch v8 for you.

### Why This?

In China, it is very difficult to compile the v8 source code. This is because the agent cannot be configured when depot_tools fetch v8, which causes the v8 download source code to be very slow or unable to download.

### How to build it?

Submit the source code directly to [dockerhub](hub.docker.com). It will automatically patch and compile source code, and then open SimpleHTTPServer for you to download. 

### How to run this docker?

docker run -it $IMAGE_NAME -p 8000:8000

