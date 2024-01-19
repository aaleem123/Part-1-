# Part-1
  Docker file Creation, GitHub and Docker Hub Integration
  
# Step 1:
 Website 
  
# Step 2:
Git, Apache2, unzip, wget, Ubuntu
  
# Step 3: Docker File

FROM ubuntu:latest
LABEL "Author"="Attia"
LABEL "Project"="app"
ENV DEBIAN_FRONTEND=noninteractive
RUN apt update && apt install git -y
RUN apt install apache2 -y
CMD ["/usr/sbin/apache2ctl", "-D", "FORGROUND"]
EXPOSE 80
WORKDIR /var/www/html
VOLUME /var/log/apache2
ADD nano.tar.gz /var/www/html
#COPY nano.tar.gz /var/www/html

  
  
# Step 4: Docker Image 
  ubuntu@ip-172-31-40-168:~/images/app$ docker build -t appimg .
[+] Building 36.3s (10/10) FINISHED                                                                        docker:default
 => [internal] load build definition from Dockerfile                                                                 0.2s
 => => transferring dockerfile: 368B                                                                                 0.0s
 => [internal] load .dockerignore                                                                                    0.1s
 => => transferring context: 2B                                                                                      0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest                                                     0.5s
 => [1/5] FROM docker.io/library/ubuntu:latest@sha256:e6173d4dc55e76b87c4af8db8821b1feae4146dd47341e4d431118c7dd060  2.7s
 => => resolve docker.io/library/ubuntu:latest@sha256:e6173d4dc55e76b87c4af8db8821b1feae4146dd47341e4d431118c7dd060  0.0s
 => => sha256:e6173d4dc55e76b87c4af8db8821b1feae4146dd47341e4d431118c7dd060a74 1.13kB / 1.13kB                       0.0s
 => => sha256:cb2af41f42b9c9bc9bcdc7cf1735e3c4b3d95b2137be86fd940373471a34c8b0 424B / 424B                           0.0s
 => => sha256:e34e831650c1bb0be9b6f61c6755749cb8ea2053ba91c6cda27fded9e089811f 2.30kB / 2.30kB                       0.0s
 => => sha256:29202e855b2021a2d7f92800619ed5f5e8ac402e267cfbb3d29a791feb13c1ee 29.55MB / 29.55MB                     0.6s
 => => extracting sha256:29202e855b2021a2d7f92800619ed5f5e8ac402e267cfbb3d29a791feb13c1ee                            1.7s
 => [internal] load build context                                                                                    0.1s
 => => transferring context: 3.03MB                                                                                  0.1s
 => [2/5] RUN apt update && apt install git -y                                                                      17.1s
 => [3/5] RUN apt install apache2 -y                                                                                11.1s
 => [4/5] WORKDIR /var/www/html                                                                                      0.2s
 => [5/5] ADD nano.tar.gz /var/www/html                                                                              0.2s
 => exporting to image                                                                                               3.9s
 => => exporting layers                                                                                              3.9s
 => => writing image sha256:ac45b445190d71aa42cb75de19683045270456efe2630d60ec48ec0acb9f50e1                         0.0s
 => => naming to docker.io/library/appimg    

 ubuntu@ip-172-31-40-168:~/images/app$ docker images
REPOSITORY    TAG       IMAGE ID       CREATED              SIZE
appimg        latest    ac45b445190d   About a minute ago   260MB
hello-world   latest    d2c94e258dcb   8 months ago         13.3kB
ubuntu@ip-172-31-40-168:~/images/app$


# Step 5:
 ubuntu@ip-172-31-40-168:~/images/app$ docker tag ac45b445190d aaleem1993/appimg:v1.0
ubuntu@ip-172-31-40-168:~/images/app$ docker push aaleem1993/appimg:v1.0
The push refers to repository [docker.io/aaleem1993/appimg]
d3251869a5ff: Pushed
5f70bf18a086: Pushed
565a54ff2b5a: Pushed
35e296605641: Pushed
8e87ff28f1b5: Mounted from library/ubuntu
v1.0: digest: sha256:78fb0a12e53415d470e38576f3ed40fa49324dd29c14c82cd90d3c36e407106f size: 1370

  

