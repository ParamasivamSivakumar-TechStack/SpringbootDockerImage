Run the Spring Boot Application in Locally.

1) Create Spring Boot Application.

2) Without Docker, create jar file and run the application through below commmands.

./mvnw package && java -jar target/gs-spring-boot-docker-0.1.0.jar

  See the result in localhost:8080 
  
If we have windows Home Edition but want to use docker..........how ?

# Create Virtualbox in Windows Machine and download docker-machine then use docker.
# Make sure Virtualbox software installed already in your windows machine.

 Docker Machine will work without Docker, but you won’t be able to use every feature of Docker Machine.
 
Now, install Docker Machine on your Linux computer with the following command:

$ base=https://github.com/docker/machine/releases/download/v0.16.0 &&
curl -L $base/docker-machine-$(uname -s)-$(uname -m) >/tmp/docker-machine &&
sudo install /tmp/docker-machine /usr/local/bin/docker-machine

Now, check whether Docker Machine is working with the following command:

$ docker-machine --version

To create a new Docker machine, run the following command:

$ docker-machine create --driver=virtualbox default (virtualbox name)

You can list all the Docker machines you’ve created so far with the following command:

$ docker-machine ls [ Note down the IP]

Paramasivam   -        virtualbox   Running   tcp://192.168.99.108:2376           v19.03.12


Connecting to Docker Machines via SSH:

Let’s say, you want to connect to the Docker machine default via SSH. To do that, run the following command:

$ docker-machine ssh default

See the docker image list

$ docker image list 

Clone the project from GIT Repository to Linux box.

git clone 'https://github.com/paramasivam2186/SpringbootDockerImage.git' [Make sure all files are copied including target folder].

Navigate to the path where Dockerfile is available.

docker@Paramasivam:~$ ls
SpringbootDockerImage

docker@Paramasivam:~$ cd SpringbootDockerImage/

docker@Paramasivam:~/SpringbootDockerImage$ ls
Dockerfile   desktop.ini  mvnw.cmd     src
HELP.md      mvnw         pom.xml      target

Below command builds an image and tags.

$ docker build -t springio/gs-spring-boot-docker .

Run the application.
$ docker run -p 8080:8080 springio/gs-spring-boot-docker

To See the dockerized application result with below url 

http://192.168.99.108:8080/

Result: "Hello Docker World"

To stop a running Docker machine default, run the following command:

$ docker-machine stop default (virtualbox name)





