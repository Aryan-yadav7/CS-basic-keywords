 # 1. Host a website using Docker and Nginx <br/>
 - Login to your AWS account and download your passkey and launch the EC2 instance.  
- Launch PuTTY and add the IP address from instance and add key pair file and open the PuTTY terminal.
- Login to the OS by writing "ubuntu"
- After that I have to install docker in my OS .<br/>
- Now install Docker using following command:
```bash
curl -sL https://github.com/ShubhamTatvamasi/docker-install/raw/master/docker-install.sh | bash
```
- Type following command to avoid using ``sudo`` always (right that's irritating)
```bash
newgrp docker
```
- Then type (This will provides a list of the Docker containers on your machine)
```bash
docker ps
```
- You can check your docker version by typing:
```bash
docker --version
```
- Now, to use ``Nginx`` in our container use the following commands:
```bash
docker pull nginx
```
```bash
docker run --name docker-nginx -p 80:80 nginx
```
### Now you can type your instance's IP and see Nginx default web page.  
- Use following command to stop the container from running:
```bash
ctrl + c
```
- Use following command to reveals that the Docker container has been exited:
```bash
docker ps -a
```
- Use following command to see container's ID
```bash
docker run --name docker-nginx -p 80:80 -d nginx
```
- Use following command to see new information about container:
```bash
docker ps
```
- Use following command to stop the container:
```bash
docker stop docker-nginx
```
- Then remove default Nginx page and create new custom html file using following commands:
```bash
docker rm docker-nginx
```
```bash
mkdir -p ~/docker-nginx/html
```
Now navigate to file created:
```bash
cd ~/docker-nginx/html
```
- Now create a ``index.html`` and write a html code on ``vim`` code editor:
```bash
vi index.html
```
- Now write your code and save the file.
Then connect the file to instance:
```bash
docker run --name docker-nginx -p 80:80 -d -v ~/docker-nginx/html:/usr/share/nginx/html nginx
```

# 2. USING MINIKUBE IN AWS

**First open aws search EC2 then Launch Instance and select 22.04 AMI then select t2.xlarge instance type then select keypair then configure storage to 30 GB then enable all traffic in network and Launch.**

**Connect it with putty and login into it by writing ubuntu**

###  write command

```
curl -sL https://github.com/ShubhamTatvamasi/docker-install/raw/master/docker-install.sh | bash
```
**it will install docker**




```
sudo usermod -aG docker $USER
```
```
newgrp docker
```

**it will Add your local user to docker group so that your local user run docker commands**






```
sudo snap install kubectl --classic
```
**it will intall kubernetes**





```
kubectl version --client
```
**it checks the version**

### Installing Minikube

```
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
```
```
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

#
#
```
minikube version
```
**it checks its version**

### Starting Minikube with Docker Driver

```
minikube start --driver=docker
```







**# If you encounter root privileges error, run:**
```
minikube start --driver=docker --force
```

```
minikube status
```
**it checks its status**







```
kubectl cluster-info
```
**it checks cluster info**



```
kubectl config view
```
**it will  show the config**







```
kubectl get nodes
```
**it will display  nodes in it**


```
kubectl get pods
```
**it will show pods in it**


```
kubectl create deployment nginx-web --image=nginx
```
```
kubectl expose deployment nginx-web --type NodePort --port=80
```
```
kubectl get deployment,pod,svc
```
**it will deploy a sample nginx deployment**


```
minikube addons list
```
**It will display all addons**







```
minikube addons enable dashboard
minikube addons enable ingress
```
**this  enables these addons**











```
minikube dashboard --url**
```
**it will get the url and run the dashboard of MiniKube**






```
kubectl proxy --address='0.0.0.0' --disable-filter=true &
```
**This will enable port :8001 to access it on your public ip**






```
http://server_ip:8001/api/v1/namespaces/kubernetes-dashboard/services/http:kubernetes-dashboard:/proxy/#/workloads?namespace=default
```
