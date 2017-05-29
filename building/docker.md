## Docker

#### General idea

* Docker is essentially a virtual machine that is very cheap to run, and very fast to start.
* Need to be aware where you are. Host or docker container.

#### Useful commands

* Installation on AWS EC2
```
[ec2-user]$ sudo yum update -y
[ec2-user]$ sudo yum install -y docker
[ec2-user]$ sudo service docker start
[ec2-user]$ sudo usermod -a -G docker ec2-user // allow ec2-user to run docker
[ec2-user]$ exit and connect again
```

* Start a container
`docker run -d container-to-be-used` 
  * The great thing about docker is that container-to-be-run is normally registered online, and can be
found automatically. The container has the instructions required to set up the environment. Normally, when it is run for the first time,
it will download an image. The next time, no need to download the image and the start up process will be very fast.
  * Everytime this command is used, a new container will be set up.
  * `-d` means deamon mode. The container is run in the background and we stay in the host.
  * If using `-it`, we will end up in the container.
  * `-rm` if using this option, the container will be removed when exit.
  * In some cases, one can add a command, normally a startup script, as part of docker run command so that the docker is up and running
  automatically.
* Manage
  * `docker ps -aq` list the id of available dockers.
  * Dockers can be access by id or name.
  * `docker stop id` stop a certain docker. data on the docker persists. Use `docker start` to start it again including whatever 
  start up script/command in the original `docker run` command.
  * `docker exec -it container-name-or-id bash` enter container-name and start bash. we end up in the container.
