# Part-1
  Docker file Creation, GitHub and Docker Hub Integration
  
# Step 1:
  root@ubuntu-focal:~# mkdir myapp
  root@ubuntu-focal:~# cd myapp
  root@ubuntu-focal:~/myapp# echo "hello World" > newapp.html
  root@ubuntu-focal:~/myapp# ls
  newapp.html
  root@ubuntu-focal:~/myapp# cat newapp.html
  hello World
  
# Step 2:
  For this part, I didnt have to install any libraries or software. I am using Ubuntu.
  
# Step 3:
  root@ubuntu-focal:~/myapp# touch dockerfile
  root@ubuntu-focal:~/myapp# ls
  dockerfile  newapp.html
  root@ubuntu-focal:~/myapp# vim dockerfile
  root@ubuntu-focal:~/myapp# cat dockerfile
  FROM nginx
  COPY newapp.html /usr/share/nginx/html
  root@ubuntu-focal:~/myapp# docker info
  root@ubuntu-focal:~/myapp# docker build -t myapp .
  
# Step 4:
   root@ubuntu-focal:~/myapp# docker build -t myapp .
   [+] Building 63.8s (7/7) FINISHED                                                                       docker:default
   => [internal] load build definition from dockerfile                                                              0.1s
   => => transferring dockerfile: 88B                                                                               0.0s
   => [internal] load .dockerignore                                                                                 0.0s
   => => transferring context: 2B                                                                                   0.0s
   => [internal] load metadata for docker.io/library/nginx:latest                                                   1.6s
   => [internal] load build context                                                                                 0.0s
   => => transferring context: 50B                                                                                  0.0s
   => [1/2] FROM docker.io/library/nginx@sha256:86e53c4c16a6a276b204b0fd3a8143d86547c967dc8258b3d47c3a21bb68d3c6   61.5s
   => => resolve docker.io/library/nginx@sha256:86e53c4c16a6a276b204b0fd3a8143d86547c967dc8258b3d47c3a21bb68d3c6    0.0s
   => => sha256:d2e65182b5fd330470eca9b8e23e8a1a0d87cc9b820eb1fb3f034bf8248d37ee 1.78kB / 1.78kB                    0.0s
   => => sha256:578acb154839e9d0034432e8f53756d6f53ba62cf8c7ea5218a2476bf5b58fc9 29.15MB / 29.15MB                 23.2s
   => => sha256:86e53c4c16a6a276b204b0fd3a8143d86547c967dc8258b3d47c3a21bb68d3c6 1.86kB / 1.86kB                    0.0s
   => => sha256:c20060033e06f882b0fbe2db7d974d72e0887a3be5e554efdb0dcf8d53512647 8.15kB / 8.15kB                    0.0s
   => => sha256:e398db710407fbc310b4bc0b0db1c94161480ac9b44638c6655939f426529780 41.38MB / 41.38MB                 57.1s
   => => sha256:85c41ebe6d660b75d8e2e985314ebce75e602330cd325bc5cfbf9d9723c329a1 627B / 627B                        0.9s
   => => sha256:7170a263b582e6a7b5f650b7f1c146267f694961f837ffefc2505bb9148dd4b0 958B / 958B                        1.8s
   => => sha256:8f28d06e2e2ec58753e1acf21d96619aafeab87e63e06fb0590f56091db38014 367B / 367B                        2.1s
   => => sha256:6f837de2f88742f4e8083bff54bd1c64c1df04e6679c343d1a1c9a650078fd48 1.21kB / 1.21kB                    3.0s
   => => sha256:c1dfc7e1671e8340003503af03d067bae6846c12c30cbc1af3e589cb124fd45d 1.40kB / 1.40kB                    3.8s
   => => extracting sha256:578acb154839e9d0034432e8f53756d6f53ba62cf8c7ea5218a2476bf5b58fc9                         3.6s
   => => extracting sha256:e398db710407fbc310b4bc0b0db1c94161480ac9b44638c6655939f426529780                         3.8s
   => => extracting sha256:85c41ebe6d660b75d8e2e985314ebce75e602330cd325bc5cfbf9d9723c329a1                         0.0s
   => => extracting sha256:7170a263b582e6a7b5f650b7f1c146267f694961f837ffefc2505bb9148dd4b0                         0.0s
   => => extracting sha256:8f28d06e2e2ec58753e1acf21d96619aafeab87e63e06fb0590f56091db38014                         0.0s
   => => extracting sha256:6f837de2f88742f4e8083bff54bd1c64c1df04e6679c343d1a1c9a650078fd48                         0.0s
   => => extracting sha256:c1dfc7e1671e8340003503af03d067bae6846c12c30cbc1af3e589cb124fd45d                         0.0s
   => [2/2] COPY newapp.html /usr/share/nginx/html                                                                  0.6s
   => exporting to image                                                                                            0.0s
   => => exporting layers                                                                                           0.0s
   => => writing image sha256:4b222ea4d311f69a4882aa9350689dbfd26e961f342ee67c827aeb401d0654c1                      0.0s
   => => naming to docker.io/library/myapp   
 
  root@ubuntu-focal:~/myapp# docker images
  REPOSITORY    TAG       IMAGE ID       CREATED          SIZE
  myapp         latest    4b222ea4d311   12 seconds ago   187MB
  hello-world   latest    9c7a54a9a43c   6 months ago     13.3kB

# Step 5:
  root@ubuntu-focal:~/myapp# docker login
  Username: aaleem1993
  Password:
  WARNING! Your password will be stored unencrypted in /root/.docker/config.json.
  Configure a credential helper to remove this warning. See
  https://docs.docker.com/engine/reference/commandline/login/#credentials-store
  
  Login Succeeded
  root@ubuntu-focal:~/myapp# docker login
  Authenticating with existing credentials...
  WARNING! Your password will be stored unencrypted in /root/.docker/config.json.
  Configure a credential helper to remove this warning. See
  https://docs.docker.com/engine/reference/commandline/login/#credentials-store
  
  Login Succeeded
  root@ubuntu-focal:~/myapp# docker push aaleem1993/newapp:v1.0
  The push refers to repository [docker.io/aaleem1993/newapp]
  d642e8122446: Pushed
  505f49f13fbe: Mounted from library/nginx
  9920f1ebf52b: Mounted from library/nginx
  768e28a222fd: Mounted from library/nginx
  715b32fa0f12: Mounted from library/nginx
  e503754c9a26: Mounted from library/nginx
  609f2a18d224: Mounted from library/nginx
  ec983b166360: Mounted from library/nginx
  v1.0: digest: sha256:36a2b5fc1751b4f855ce4c98e077c53405535fe23017dcd411507defc56ea943 size: 1985
  
  Successful pushed:
  Docker Pull Command:  docker pull aaleem1993/newapp  
