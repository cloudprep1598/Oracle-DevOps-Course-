# Oracle-DevOps-Course-

OCI Devops as a service 

<img width="762" height="356" alt="image" src="https://github.com/user-attachments/assets/9445858a-d6c4-44ec-b36b-b4f70022e41a" />

OCI Devops as a service benefits

<img width="731" height="412" alt="image" src="https://github.com/user-attachments/assets/163fd8f1-267c-4c43-9a08-914f9da66442" />

# Case study : 
Developing Cloud native solutions on OCI 
STEP 1 

<img width="602" height="381" alt="image" src="https://github.com/user-attachments/assets/78690c20-f072-4cf1-93e1-791595ac615c" />

STEP 2

<img width="708" height="365" alt="image" src="https://github.com/user-attachments/assets/371a6010-1250-4443-8fab-221f62730261" />

STEP 3 


<img width="737" height="383" alt="image" src="https://github.com/user-attachments/assets/37a842d6-ac52-4d22-996a-ff6560ef233a" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d7c2cc2f-8e47-4901-856c-5c166c11dfdc" />



-------------------------------------------------------------------------------------------------

# what are microservices 
- in microservices architecture , each micsroservices owns a simple task and communicates with clients or other microservices by using lightweight communication mechanism such as REST APU request
- microservices are used to design and application that is
      - multilingual
      - loosely coupled with other services
      - easy to maintain and independently deployable
      - easily scalable and highly available
      - failures resistant
example of microservices architecture
<img width="722" height="380" alt="image" src="https://github.com/user-attachments/assets/0244360c-fdca-4036-a7ae-a56726f98d9d" />



# monolethic vs microservice architecture

<img width="698" height="417" alt="image" src="https://github.com/user-attachments/assets/145eb95f-5931-4e2d-ac7b-f3d1984828c1" />

# difference between monolethic vs microservice architecture

<img width="942" height="543" alt="image" src="https://github.com/user-attachments/assets/83947384-7bf1-48a4-9256-2505122ca442" />

# communication mechanism in a microservices architecture 

<img width="775" height="417" alt="image" src="https://github.com/user-attachments/assets/ffd6e337-12c7-4e75-a57e-6697886ad676" />

-----------------------------------------------------------------------------------------------

# Design methodology of microservices 
 12 factor methodology for developing microservice based applications 
1. codebase
2. dependencies
3. configuration
4. backing services
5. build , release and run
6. processes
7. port binding
8. concurrency
9. desposability
10. development and production parity
11. logs
12. admin processes

# Microservices design : benefits 
1. easier to build and maintain apps
2. oragnized around bisuness capabilities
3. improved productivity and speed of deployment
4. increased fault tolerance and fault isolation
5. greater scalability and flexibility
6. simplified security monitoring
7. autonomous , crosss functional teams

# Microservices design : drawbacks
1. more complex
2. more expensive then monoliths
3. require cultural changes
4. present harder debugging problems
5. global testing is difficult
----------------------------------------------------------------------------------------



# Introduction to containerization ?

# what is containerization ?
- with containerization , create a unified software packages (container)
- this technique brings virutlization at the operating system level
- container engine serves as the runtime environment
- containers shared the host os and hold only application and realted binaries
- containerized applications seamlessly run on various devices and os 

<img width="397" height="400" alt="image" src="https://github.com/user-attachments/assets/7d3f6b4a-a906-46ff-942b-e32aa2fbcff6" />

# How it is different from virtualization ?

- continerization reduces startup overhead and eliminates the need for individual guest os setup by sharing the same os kernel
- it efficiently packages microservies enhancing resource use and enabling agile deployments

  
<img width="756" height="406" alt="image" src="https://github.com/user-attachments/assets/d6f9bc6a-86b1-476a-9a52-5b2075a9c8b3" />
  


# benefits of containerization 
1. it provides portability
2. agility
3. speed
4. fault isolation
5. efficiency
6. ease of management
7. security


------------------------------------------------------------------------------------------------

# Docker components 

Docker client - 
Docker daemon
docker registry 


<img width="745" height="403" alt="image" src="https://github.com/user-attachments/assets/ffa4bce4-fc8d-470d-a777-82b449e667dd" />

# virtual machines vs containers 

<img width="660" height="302" alt="image" src="https://github.com/user-attachments/assets/eafbe15c-0c18-48d5-9fc3-8971035210f5" />


# basic docker commands 

<img width="738" height="367" alt="image" src="https://github.com/user-attachments/assets/b80ed13c-4edb-43f3-9bf6-d5c8854892fa" />

----------------------------------------------------------------------------------------------

Docker basic commands  that we will used 

<img width="450" height="516" alt="image" src="https://github.com/user-attachments/assets/d5c793af-657a-4f3d-b1b3-919631ae3e36" />


-----------------------------------------------------------------------------------------------

Dockerfile 



----------------------------------------------------------------------------------------------

Hands on lab : working with docker images and repository
1. go to cloud shell
2. we have created docker images for python application and coantienrize it 
3. create one python file naming app.py and one dockerfile which is helps us to create a container 
4. app.py file contains 
**from flask import Flask
import os
import socket

app = Flask(__name__)
app.route("/")

def hello():
    html = "<h3>Hello {name}!</h3>" \
           "<b>Hostname:</b> {hostname}<br/>"
    return html.format(name=os.getenv("NAME", "world"), hostname=socket.gethostname())

if __name__ == "__main__":
    app.run(host='0.0.0.0', port=4000)**

Flask: The web framework used to create the web server.

os: Used to access environment variables.

socket: Used to get the hostname of the running machine.

Flask(__name__): Initializes a Flask application, where __name__ tells Flask where to look for resources (like templates and static files).

@app.route("/"): Decorator to define the root URL ("/") for the app.

hello(): Function that runs when the root URL is accessed.

html format string: Displays a greeting with the user’s name and the hostname.

os.getenv("NAME", "world"): Fetches the NAME environment variable or defaults to "world" if not set.

socket.gethostname(): Gets the hostname of the current server/machine.

Return: Sends the formatted HTML back to the user’s browser.

Ensures the application runs only if the script is executed directly (not imported).

app.run(host='0.0.0.0', port=4000): Starts the Flask app, accessible on all network interfaces at port 4000.

The "World" can be replaced by setting the NAME environment variable in your environment or Docker container.



5.Dockerfile contains 
**FROM python:2.7-slim
WORKDIR /app
COPY . /app
RUN pip install --trusted-host pypi.python.org Flask
EXPOSE 80
ENV NAME World
CMD ["python", "app.py"]**

This Dockerfile:

Uses Python 2.7 slim base image

Sets working directory to /app

Copies current directory contents to /app

Installs Flask using pip

Exposes port 80

Sets environment variable NAME to "World"

Runs the app.py file when container starts


6. build a docker image from dockerfile

   docker build -t kaustubh-demo1 .

7.check the images 

 docker images 

8.containerized the docker image 

docker run --name OCI-webapp -p 8080:4000 kaustubh-demo1

now contianer is running 

9. check the container is running using below command

 docker ps

10.using curl command to check output 

cutl http://127.0.0.1:8080

we are getting hello world output

11. pull an image from dockerhub and push an image to dockerhub

For Pull ,
docker pull [image name from dockerhub]

for push ,
create one repo on dockerhub
after creation , 

go to cli , and check docker images 
go to cli , give tag to the image which is to be push to dockerhub

use below command to give tag and ist of images :

docker tag kaustubh-demo1 repo1/oci-demo:v1 
docker images 

you will get another image with above name
 
for push , 
use command : docker login 
enter username and password 
use command for push : docker push repo1/oci-demo:v1 
check the image on dockerhub

delete an image using below commnds :
docker images 
docker rmi [image id]


------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------



Introduction to Oracle cloud infrastructure registry : introduction 
OCIR 
- Oracle managed registry
- enables easy storage , sharing and maangement of container images
- support pushing and pulling container images via cli from private and public OCIR repositories
- complian with open container initiative standards
- support for multi architecture images
- support private access from oracle cloud infra resources in virtual cloud network through a service gateway

benefits 
- integration
- security
- regional availability
- high availability
- anywhere access
- repository quotas

**container registry concepts **
1. images
   - it is read only template with instructions for creating a container
   - hold the applications that you want to run as a container and along with any dependencies
   - store any artifacts such as docker images , manifest list , helm charts
  
2. repository
   - it is a meaningfully named collection of related images
   - different version of same source images are grouped into same repository
   - repository can be private or public
   - user needs OCI credentials to push/pull image from  OCIR Repo
  
3. region key
4. repository name
5. tenancy namespace
6. registry identifier   <region-key>.ocir.io/<tenancy-namespace>
7. tag
8. image name  <repo-name>:<tag>
9. image path  <region-key>.ocir.io/<tenancy-namespace>/<repo-name>:<tag>

-------------------------------------------------------------------------------------------

Managing OCIR 

1. managing repository
- creating repository
- deleting a repository (taken 48 hours to delete completely)
- moving repo between compartments

2. managing images
- vieving images and image details
- pushing /pulling images from docker cli
- deleting and undeleting an image
- retaining and deleting images using retention policies - global retention policies and custom retention policies
- untagging images
- pulling images from container registry during k8s deployment
           - use kubectl to create a docker registry secret
           - specify the image locaion in OCIR and the docker secret in deployment manifest file 

  
3. managing security
- policies to control repo access
  
  <img width="209" height="57" alt="image" src="https://github.com/user-attachments/assets/f91f6dc8-2e28-44a6-a61a-835987c8737f" />

- getting an auth token
- scanning images for vulnerabilities



**Preparing for container registry **

<img width="345" height="130" alt="image" src="https://github.com/user-attachments/assets/6c4ea043-b441-450a-b38a-2c1a2819f513" />

**Demo on Managing OCIR :**
step 1 
go to registry service by specific cloud provider 
click on create repository name and make sure it is uniqe 
make them private or public as per the requirement 

step 2 push image to repo 
for push image you required auth token and create one auth token 

step 3 go to docker client machine 
docker login region code 
enter username and password 

step 4 push images to container registry 
docker images
docker tag [image name of your machine] [container registry new name of image:version]
docker push [image name with tag]

step 5 delete images in local machine
docker rmi -f ed4   forcefully deleted all images in loal machine

step 6 pull images from container registry 
docker pull [container registry image name]


