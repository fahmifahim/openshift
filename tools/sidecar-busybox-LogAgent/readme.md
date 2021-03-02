```bash
#Create project directory.
mkdir custom-busybox
cd custom-busybox

#Prepare your Dockerfile

#Use docker build command to build the image. 
#This example names the image as custom-busybox:latest
docker build -t custom-busybox:v1.32.1 ./

#Check the newly created custom-busybox image
docker images
        REPOSITORY                        TAG       IMAGE ID       CREATED         SIZE
        busybox                           latest    491198851f0c   11 days ago     1.23MB

#Save the image to local 
docker save -o /home/user1/fluentd.tar fluent/fluentd:latest

ls -l /home/user1/fluentd.tar

#Copy the image to your remote server
scp /home/user1/fluentd.tar root@remote-server-ip:/home/user1/

#Load image from local file at your remote server
docker load -i /home/user1/fluentd.tar
        df64d3292fd6: Loading layer [==================================================>]  4.672MB/4.672MB
        91d1787a48d9: Loading layer [==================================================>]  38.35MB/38.35MB
        4c1e27ed455f: Loading layer [==================================================>]  2.048kB/2.048kB
        2bf9e4461d5c: Loading layer [==================================================>]   2.56kB/2.56kB
        96049201c093: Loading layer [==================================================>]  3.584kB/3.584kB
        cc1df1d557f2: Loading layer [==================================================>]  3.072kB/3.072kB
        e129090bea45: Loading layer [==================================================>]  3.072kB/3.072kB
        Loaded image: fluent/fluentd:latest

```
