# DSC #

Docker Swarm Compose (DSC) should be unpacked into its constituent components. Whereas Docker run can indeed start up a container, Docker Compose can be utilized to start up multi-container applications. As should be clear, Docker Compose can be more efficient than using Docker run, particularly when there might be a plethora of containers to start up.

Monolithic applications have been restructured as microservices application, wherein each microservice has a different logical function for the involved application. The microservices reside in containers (packages that include everything needed to run). Docker and Kubernetes have been the more popular of the container orchestration frameworks to handle multiple containers.

Docker is a set of components. Among these, there are two tool components: (1) Docker Compose, and (2) Docker Swarm.

Docker Compose is the container orchestration component of the Docker ecosystem. Container orchestration involves configuring and managing a group of related containers.

Docker Swarm is the scheduling component of the Docker ecosystem. Scheduling involves determining where to place the containers within the cluster of Docker hosts.

 You can have a cluster of hundreds of servers, and you may have hundreds of containers, each encapsulating a service for a dozen different applications. Now how should these containers be distributed across your cluster of hundreds of servers, should some containers be placed only on certain hosts because they satisfy a particular criteria or maybe they should be closer to (or not) other containers which are somehow related... all these are part of the scheduling component which is performed by docker Swarm.



docker-compose: Command used to configure and manage a group of related containers. It is a frontend to the same api's used by the docker cli, so you can reproduce it's behavior with commands like docker run.
docker-compose.yml: Definition file for a group of containers, used by docker-compose and now also by swarm mode.
swarm mode: Used to manage a group of docker engines as a single entity and provide orchestration (constantly trying to correct any differences between the current state and the target state).
service: One or more containers for the same image and configuration within swarm, multiple containers provide scalability.
stack: One or more services within a swarm, these may be defined using a DAB or a docker-compose.yml file.
bridge network: Network managed by a single docker engine where multiple containers may communicate with each other. You may have multiple networks managed by an engine, and containers can be attached to zero or more networks.
overlay network: Similar to a bridge network but spanning multiple docker engines. These require a key/value store to maintain their state. Swarm mode provides this, but if swarm mode is disabled, you may also use etcd, consul, or zookeeper.
links: a method to connect containers together that predates the bridged network. Its usage is no longer recommended.
classic swarm: A predecessor to the integrated swarm mode that runs as a container, allows multiple engines to appear as one, but does not provide orchestration or include its own k/v store.
