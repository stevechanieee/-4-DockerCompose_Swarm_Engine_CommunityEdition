# Docker Compose, Swarm #

Whereas the utilization of *docker run* can indeed start up a container, Docker Compose can be utilized to start up multi-container applications. As should be clear, Docker Compose can be more efficient than using *docker run*, particularly when there might be a plethora of containers to start up.

In contemporary times, monolithic applications have been restructured as microservices applications, wherein each microservice has a different logical function for the involved application. The microservices reside in containers (packages that include everything needed to run). Historically, Docker and Kubernetes have been the more popular of the container orchestration frameworks to handle multiple containers.

Docker is a set of components. Among these, there are two core tool components: (1) Docker Compose, and (2) Docker Swarm.

Docker Compose is the configuration component of the Docker ecosystem. The core function centers upon configuring and managing a group of related containers.

Docker Swarm is the scheduling component of the Docker ecosystem. The core function centers upon determining where to place the containers within the cluster of Docker hosts (a physical computer system or a virtual machine running Linux).

The advantages of Docker Swarm become quite evident when there is a cluster of hundreds/thousands of servers. Presuming that this paradigm equates to hundreds/thousands of container, wherein each container encapsulates a service, which might be utilized by any number of applications, the question becomes how these containers should be optimally distributed thoughout the cluster. Among other considerations, some containers are more intricately linked to other containers, and this begets the question of whether these containers should be co-located on certain Docker hosts or, at the very least, be in close proximity. These optimization problems reside within the rubric of the scheduling component, which is performed by Docker Swarm.

*Source: https://codefresh.io/docker-tutorial/docker-machine-basics/*

For the purposes of disambiguation, please note that Docker Swarm is distinct and disparate from Swarmkit. For convenience, please find the distinctions below:

Docker Swarm (a.k.a. Classic Swarm or Swarm Class standalone) refers to the older (2014 initial release) native clustering system for Docker. It serves to connect Docker hosts and turn them into a single, virtual host (via an API). As note by this page, https://github.com/docker/classicswarm, it "has been archived and is no longer actively developed. You may want to use the Swarm mode built into the Docker Engine instead, or another orchestration system."



Swarmkit is a cluster management and orchestration feature (2016 initial release), which stemmed from Docker's acquisition of Software-Defined Networking (SDN) technology firm SocketPlane. Swarmkit has been available in Docker Engine v1.12 or higher.

*Source: https://thenewstack.io/docker-acquires-sdn-technology-startup-socketplane-io/*

For convenience, please find the Docker Engine release versions below in Table 1: 

### Table 1: Docker Engine Release Version Information ###




Docker Swarm Mode refers to the which are now built into Docker itself to allow you to initiate a new Swarm and deploy tasks (which are Docker containers in this case, but don't have to be, see Swarmkit above) to that cluster.

*Source: https://stackoverflow.com/questions/38474424/the-relation-between-docker-swarm-and-docker-swarmkit?answertab=active#tab-top*


In Docker v1.12 and higher, Swarm mode is integrated with Docker Engine



*Source: https://thenewstack.io/kubernetes-vs-docker-swarm-whats-the-difference/*




provides native clustering functionality for Docker containers, which turns a group of Docker engines into a single virtual Docker engine.[55] 

docker-compose: Command used to configure and manage a group of related containers. It is a frontend to the same api's used by the docker cli, so you can reproduce it's behavior with commands like docker run.
docker-compose.yml: Definition file for a group of containers, used by docker-compose and now also by swarm mode.
swarm mode: Used to manage a group of docker engines as a single entity and provide orchestration (constantly trying to correct any differences between the current state and the target state).
service: One or more containers for the same image and configuration within swarm, multiple containers provide scalability.
stack: One or more services within a swarm, these may be defined using a DAB or a docker-compose.yml file.
bridge network: Network managed by a single docker engine where multiple containers may communicate with each other. You may have multiple networks managed by an engine, and containers can be attached to zero or more networks.
overlay network: Similar to a bridge network but spanning multiple docker engines. These require a key/value store to maintain their state. Swarm mode provides this, but if swarm mode is disabled, you may also use etcd, consul, or zookeeper.
links: a method to connect containers together that predates the bridged network. Its usage is no longer recommended.
classic swarm: A predecessor to the integrated swarm mode that runs as a container, allows multiple engines to appear as one, but does not provide orchestration or include its own k/v store.
