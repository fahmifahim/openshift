
#### Preparation  
```bash
#Create project directory.
mkdir custom-busybox
cd custom-busybox

#Prepare your Dockerfile

#Use docker build command to build the image. 
#This example names the image as custom-busybox:latest
docker build -t custom-busybox:v1.32.1 ./
        Sending build context to Docker daemon  498.7kB
        Step 1/2 : FROM busybox:latest
        ---> 491198851f0c
        Step 2/2 : COPY ./rsync /bin/rsync
        ---> 036d1070db5c
        Successfully built 036d1070db5c
        Successfully tagged custom-busybox:v1.32.1

#Check the newly created custom-busybox image
docker images
        REPOSITORY                        TAG       IMAGE ID       CREATED          SIZE
        custom-busybox                    v1.32.1   036d1070db5c   34 seconds ago   1.73MB

#(OPTIONAL)Save the image to local 
docker save -o /home/user1/custom-busybox.tar custom-busybox:v1.32.1

ls -l /home/user1/custom-busybox.tar

#(OPTIONAL)Copy the image to your remote server
scp /home/user1/custom-busybox.tar root@remote-server-ip:/home/user1/

#Load image from local file at your remote server
docker load -i /home/user1/custom-busybox.tar
        6fac254bbae9: Loading layer [==================================================>]  498.2kB/498.2kB
        Loaded image: custom-busybox:v1.32.1
```  

#### Test your image  
```bash
#Create pod using log-counter-busybox.yaml
kubectl create -f log-counter-busybox.yaml -n dev-namespace
        pod/counter-customized created

kubectl get pod -n dev-namespace
        NAME                 READY   STATUS    RESTARTS   AGE
        counter-customized   1/1     Running   0          91s


```
