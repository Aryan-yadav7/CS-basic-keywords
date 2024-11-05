# Cloud Computing 
cloud computing is the delivery of computing services—including servers, storage, databases, networking, software, analytics, and intelligence—over the internet (“the cloud”) to offer faster innovation, flexible resources, and economies of scale.
![17307774414418712033551721005272](https://github.com/user-attachments/assets/0859bf58-0ace-4419-aac2-f4696f2b21dd)
# Docker
Docker is a software platform that allows you to build, test, and deploy applications quickly. Docker packages software into standardized units called containers that have everything the software needs to run including libraries, system tools, code, and runtime.
![image](https://github.com/user-attachments/assets/81a19615-dbd6-4979-869b-c21f49255b4b)
# HOW TO INSTALL DOCKER:- 

To install Docker on a remote server using PuTTY, you'll first need to ensure you have access to a Linux server (like Ubuntu, CentOS, etc.) via SSH. Here's a step-by-step guide:

## Step 1:Connect to Your Server


## Step 2: Update Your Package Index

Before installing Docker, it’s a good idea to update the package index:

```bash
sudo apt update
```


## Step 3:Install Prerequisites

For Ubuntu, install the required packages:

```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```

For CentOS, run:

```bash
sudo yum install -y yum-utils
```

## Step 4: Add Docker’s Official GPG Key

For Ubuntu:

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

For CentOS:

```bash
sudo rpm --import https://download.docker.com/linux/centos/gpg
```

## Step 5: Set Up the Stable Repository
For Ubuntu:

```bash
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```


For CentOS:

```bash
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```

## Step 6: Install Docker

For Ubuntu:

```bash
sudo apt update
```

```bash
sudo apt install docker-ce
```

For CentOS:

```bash
sudo yum install docker-ce
```

## Step 7: Start Docker

Enable and start the Docker service:


```bash
sudo systemctl start docker
```

```bash
sudo systemctl enable docker
```

## Step 8: Verify the Installation

Check if Docker is running:

```bash
sudo systemctl status docker
```

You can also run a test container:

```bash
sudo docker run hello-world
```

## Step 9: (Optional) Manage Docker as a Non-Root User

If you want to run Docker commands without sudo, add your user to the 

Docker group:

```bash
sudo usermod -aG docker $USER
```

After running this command, log out and back in for the changes to take effect.

# Conclusion

You’ve successfully installed Docker using PuTTY! If you have any questions or run into issues, feel free to ask.

# container:-

A container is a standard unit of software that packages up code and all its dependencies so the application runs quickly and reliably from one computing environment to another. A Docker container image is a lightweight, standalone, executable package of software that includes everything needed to run an application: code, runtime, system tools, system libraries and settings.

(in other and simple words )

Containers are an abstraction at the app layer that packages code and dependencies together. Multiple containers can run on the same machine and share the OS kernel with other containers, each running as isolated processes in user space. Containers take up less space than VMs (container images are typically tens of MBs in size), can handle more applications and require fewer VMs and Operating systems

![Screenshot_2024_0918_124201](https://github.com/user-attachments/assets/6f6cd7ae-eee7-4b0b-b614-313b4e8000bd)
# NGINX:-

NGINX is a high-performance web server and reverse proxy server that is widely used for serving web applications, handling HTTP and HTTPS requests, and load balancing traffic. It is known for its speed, efficiency, and ability to handle a large number of concurrent connections with low resource usage.

![Screenshot_2024_0918_140523](https://github.com/user-attachments/assets/ff5971c8-d6b8-434e-b93a-8476dc5a8f83)

# HOW TO INSTALL NGINX :-
In this tutorial, we’ll show you how to install NGINX on Linux.

## Open your Linux machine and run an update using the command below:

```bash
sudo apt-get update
```

Next, run this command:

```bash
sudo apt-get install nginx
```

## Then, enable your firewall with the following:

```bash
sudo ufw enable
```

## To verify NGINX is installed, run the following:

```bash
nginx -v
```

## You can run the command below to find out if NGINX is running:

```bash
sudo ufw status
```

After running this command, you should see the following:

status: active

## To check whether your NGINX server is working fine, run the following:

```bash
sudo systemctl status nginx
```

# using EC2 in aws:-

First open aws search EC2 then Launch Instance and there select keypair in putty then download it

after that Launch it and run putty and paste public id on HOST NAME and open that downloaded key pair for putty in SSH then Auth then Credentials and open there

## after that run it and write username as ubuntu as selected os and then type following commands

```bash
sudo apt update
```


```bash
sudo apt install apache2
```

## to install a web server on ip then

```bash
sudo su
```

## for convert $ into # for getting admin role then

```bash
cd /var/www/html/
```

##then

```bash
ls
```

## for list of html file in it

## then copy that html file name and write

```bash
rm index.html
```

```bash
rm means remove command
```

```bash
vi index.html
```

## this will open a notepad like and write html code there like (vi is editor) -

## then press ctrl+c then shift+colon then write wq and enter

## now copy your public ip and paste it on browser you will see the texts written by you (by using html above)



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
# VPC

Amazon Virtual Private Cloud (VPC) is a virtual network that allows users to launch AWS resources in a logically isolated environment. It's a foundational service of AWS that gives users complete control over their virtual networking environment. 

### What is the difference between EC2 and VPC?

•EC2 is a virtual server that you can run your software on. VPC is a virtual network that you use to connect your virtual servers, and other resources.

### Go to VPC and create a VPC then we  have to create 4 subnets , where 2     subnets are private and other two are  public .

![Screenshot_2024_1104_181237](https://github.com/user-attachments/assets/25f8774d-56f0-426e-8cf2-eee68511767e)


![Screenshot_2024_1104_181126](https://github.com/user-attachments/assets/0512bbc2-f00c-4f5e-b853-63032d26e6e1)

## create  gateways:- 

 1st  create INTERNET GATWAY , whic is  to be connected to your VPC which is   created earliy.

![Screenshot_2024_1104_181831](https://github.com/user-attachments/assets/a3bb96a9-b738-4031-a65b-d169b25fd263)


•2nd we have to create VPG virtual      privaye gate, and connect to VPC .

## create route tables 

•Now we have to go to the route table   and create 2 route table , one for     IGW and another for VGW .

![Screenshot_2024_1104_181847](https://github.com/user-attachments/assets/77c3730e-5cf4-4a0d-a78d-ac070f231688)

•Now we have to connect two public      subnet in myigw and on other we have   to add the private subnets .

![Screenshot_2024_1104_182425](https://github.com/user-attachments/assets/555833f8-2889-4028-b563-89596c844143)

## create instances

• now we have to create two instnaces    where we have to enable the public     IPv4 .

•then on both instance we have to       downlaod the web server here i have    downlaoded the apache2 server

-- after that i chech that my             instances are working or not .

![Screenshot_2024_1104_182258](https://github.com/user-attachments/assets/c913fb61-bc91-43d2-bd2a-47fdba5e508e)

## now we have to create the load         balancer

--where we have to give vpc, aviablity   zone of the ec2 instance

•then we have to create the target      group where we have to select the two  insatance we have create then we have  to go to helath check edited option    which was present below the load       balancer is create ,then edit it as    given below image


![Screenshot_2024_1104_182902](https://github.com/user-attachments/assets/0ae0ab8a-9196-486b-ad41-b9e27c901240)

•after that come to load balancer       where we have to select the target     group which we have created then make  the load balancer , it will look like  the given image below .

![Screenshot_2024_1104_183106](https://github.com/user-attachments/assets/a891ba72-6a20-4f33-89c2-cbe07cd88904)

![Screenshot_2024_1104_183126](https://github.com/user-attachments/assets/1c5a8cf9-ff8d-4565-8968-7d1c0df5920a)

*now put on any one instance write following commands in putty -*

* ```
  htop
  ```
  ```
  seq 999999999999999999999999999999999999999999999999999999999 > /dev/null &
  ```
  ```
  htop
  ```

  ![Screenshot_2024_1104_183758](https://github.com/user-attachments/assets/bae13bf3-7e99-4944-86fb-156efc303382)

### book link for reference of VPC given below (page 55 )

{ https://www.scribd.com/document/454176546/AWS-lab-practice-guide-by-www-server-computer-com-v1
}


![Screenshot_2024_1105_055750](https://github.com/user-attachments/assets/268cad3b-5081-4e9b-9f17-a5aa70d6de41)


# NETWORKING 

![Screenshot_2024_1105_055827](https://github.com/user-attachments/assets/e060004d-ad36-482b-9128-ad60ad5ee88a)


## what is client and server 
( below image shows this )

![Screenshot_2024_1105_050813](https://github.com/user-attachments/assets/6246f115-7109-4ec4-87a4-e466770f5e7c)


### types of network 

![Screenshot_2024_1105_071234](https://github.com/user-attachments/assets/756402b9-6449-449b-aa2f-5ed46c23f185)

![Screenshot_2024_1105_050930](https://github.com/user-attachments/assets/1bfa85e4-0476-4afa-ba21-d909617fbffa)
