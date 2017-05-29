## Set up data science stack on EC2

#### EC2 and docker

* A good [reference](http://www.ybrikman.com/writing/2015/11/11/running-docker-aws-ground-up/#deploying-docker-containers-manually) to get started.
* Launch a EC2 server, install docker.
* Generated key file. If using Putty, need to use Puttygen to convert pem to ppk.

#### Data science stack

* I forked this [container](https://github.com/jupyter/docker-stacks).
* It includes a lot of useful containers.
* How to run datascience-notebook
```
docker run -d -p 8888:8888 jupyter/datascience-notebook start-notebook.sh --NotebookApp.token='XXX'

```
