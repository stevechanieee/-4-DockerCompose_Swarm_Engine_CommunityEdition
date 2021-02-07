# Docker Compose, Swarm, Engine, Community Edition #

Whereas the utilization of *docker run* can indeed start up a container, Docker Compose can be utilized to start up multi-container applications. As should be axiomatic, Docker Compose can be more efficient than using *docker run*, particularly when there might be a plethora of containers to start up.

In contemporary times, monolithic applications have been restructured as microservices applications, wherein each microservice has a different logical function for the involved application. The microservices reside in containers (packages that include everything needed to run). Historically, Docker and Kubernetes have been the more popular of the container orchestration frameworks to handle multiple containers. Also, historically, Docker was a set of components. Among these, there were two core tool components: (1) Docker Compose, and (2) Docker Swarm.

Docker Compose was the configuration component of the Docker ecosystem. The core function centers upon configuring and managing a group of related containers.

Docker Swarm was the scheduling component of the Docker ecosystem. The core function centers upon determining where to place the containers within the cluster of Docker hosts (a physical computer system or a virtual machine running Linux).

The advantages of Docker Swarm become quite evident when there is a cluster of hundreds/thousands of servers. Presuming that this paradigm equates to hundreds/thousands of containers, wherein each container encapsulates a particular service, which might be utilized by any of a number of applications, the question centers upon how these containers should be optimally distributed thoughout the cluster. Among other considerations, some containers are more intricately linked to other containers, and this begets the question of whether these containers should be co-located on certain Docker hosts or, at the very least, be in close proximity. These optimization problems reside within the rubric of the scheduling component, which is performed by Docker Swarm.

*Source: https://codefresh.io/docker-tutorial/docker-machine-basics/*

For the purposes of disambiguation, please note that Docker Swarm is distinct and disparate from Swarmkit. For convenience, please find the distinctions below:

Docker Swarm (a.k.a. Classic Swarm or Swarm Class standalone) refers to the older (2014 initial release) native clustering system for Docker. It serves to connect Docker hosts and turn them into a single, virtual host (via an API). As note by this page, https://github.com/docker/classicswarm, it "has been archived and is no longer actively developed. You may want to use the Swarm mode built into the Docker Engine instead, or another orchestration system."

*Source: https://github.com/docker/classicswarm*

Swarmkit is a cluster management and orchestration feature (2016 initial release), which stemmed from Docker's acquisition of Software-Defined Networking (SDN) technology firm SocketPlane. Swarmkit has been available in Docker Engine v1.12 or higher.

*Source: https://thenewstack.io/docker-acquires-sdn-technology-startup-socketplane-io/*

For convenience, please find the Docker Engine release versions below in Table 1: 

### Table 1: Docker Community Edition (as of March 2017)/Docker Engine Version Information ###

| Docker Major Release Version | Minor Release Version | Release Date |
|--------------------------------------|-----------------------|--------------|
| 19.03                                | 19.03.15              | 2/1/21       |
|                                      | 19.03.14              | 12/1/20      |
|                                      | 19.03.13              | 9/16/20      |
|                                      | 19.03.12              | 6/18/20      |
|                                      | 19.03.11              | 6/1/20       |
|                                      | 19.03.10              | 5/29/20      |
|                                      | 19.03.9               | 5/14/20      |
|                                      | 19.03.8               | 3/10/20      |
|                                      | 19.03.7               | 3/3/20       |
|                                      | 19.03.6               | 2/12/10      |
|                                      | 19.03.5               | 11/14/19     |
|                                      | 19.03.4               | 10/17/19     |
|                                      | 19.03.3               | 10/8/19      |
|                                      | 19.03.2               | 9/3/19       |
|                                      | 19.03.1               | 7/25/19      |
|                                      | 19.03.0               | 7/22/19      |
| 18.09                                | 18.09.9               | 9/3/19       |
|                                      | 18.09.8               | 7/17/19      |
|                                      | 18.09.7               | 6/27/19      |
|                                      | 18.09.6               | 5/6/19       |
|                                      | 18.09.5               | 4/11/19      |
|                                      | 18.09.4               | 3/28/19      |
|                                      | 18.09.3               | 2/28/19      |
|                                      | 18.09.2               | 2/11/19      |
|                                      | 18.09.1               | 1/9/19       |
|                                      | 18.09.0               | 11/8/18      |
| 18.06                                | 18.06.3-ce            | 2/19/19      |
|                                      | 18.06.2               | 2/11/19      |
|                                      | 18.06.1-ce            | 8/21/18      |
|                                      | 18.06.0-ce            | 7/18/18      |
| 18.05                                | 18.05.0-ce            | 5/9/18       |
| 18.04                                | 18.04.0-ce            | 4/10/18      |
| 18.03                                | 18.03.1-ce            | 4/26/18      |
|                                      | 18.03.0-ce            | 3/21/18      |
| 18.02                                | 18.02.0-ce            | 2/7/18       |
| 18.01                                | 18.01.0-ce            | 1/10/18      |
| 17.12                                | 17.12.1-ce            | 2/27/18      |
|                                      | 17.12.0-ce            | 12/27/17     |
| 17.11                                | 17.11.0-ce            | 11/20/17     |
| 17.10                                | 17.10.0-ce            | 10/17/17     |
| 17.09                                | 17.09.1-ce            | 12/7/17      |
|                                      | 17.09.0-ce            | 9/26/17      |
| 17.07                                | 17.07.0-ce            | 8/29/17      |
| 17.06                                | 17.06.2-ce            | 9/5/17       |
|                                      | 17.06.1-ce            | 8/15/17      |
|                                      | 17.06.0-ce            | 6/28/17      |
| 17.05                                | 17.05.0-ce            | 5/4/17       |
| 17.04                                | 17.04.0-ce            | 4/5/17       |
| **17.03**                                | **17.03.3-ce**            | 8/30/18      |
|                                      | **17.03.2-ce**            | 5/29/17      |
|                                      | **17.03.1-ce **           | 3/27/17      |
|                                      | **17.03.0-ce**            | 3/1/17       |
| 1.13                                 | 1.13.1                | 2/8/17       |
|                                      | 1.13.0                | 1/18/17      |
| **1.12**                                 | **1.12.6**                | 1/10/17      |
|                                      | **1.12.5**                | 12/15/16     |
|                                      | **1.12.4**                | 12/12/16     |
|                                      | **1.12.3**                | 10/26/16     |
|                                      | **1.12.2**                | 10/11/16     |
|                                      | **1.12.1**                | 8/18/16      |
|                                      | **1.12.0**                | 7/28/16      |
| 1.11                                 | 1.11.2                | 5/31/16      |
|                                      | 1.11.0                | 4/13/16      |

*Source: https://docs.docker.com/engine/release-notes/19.03/*

Docker Engine release versions start at 0.1.0 with a release date of 3-23-13. Table 1 shows back to v1.11 for the purposes of showing the iinflection point between v1.11 and v1.12, as it should be noted that for v1.12 and higher, Swarm mode is integrated with Docker Engine. In addition, the documentation notes that "Docker CE 17.11 is the first Docker release based on containerd 1.0 beta. Docker CE 17.11 and later don’t recognize containers started with previous Docker versions. If using Live Restore, you must stop all containers before upgrading to Docker CE 17.11. If you don’t, any containers started by Docker versions that predate 17.11 aren’t recognized by Docker after the upgrade and keep running, un-managed, on the system." Finally, Docker Engine was renamed to Docker Community Edition (Docker CE) in March 2017. Before March 2017, the latest version of Docker that was available at the time was v1.13. After the rollout of Docker CE (with the simultaneous rollout of Docker Enterprise Edition, which will not be discussed in this thread), the release version number jumped to 17.03.

*Source: https://docs.docker.com/engine/release-notes/17.11/*
*Source: https://boxboat.com/2018/12/07/docker-ce-vs-docker-ee/*



Docker Swarm Mode refers to the which are now built into Docker itself to allow you to initiate a new Swarm and deploy tasks (which are Docker containers in this case, but don't have to be, see Swarmkit above) to that cluster.

*Source: https://stackoverflow.com/questions/38474424/the-relation-between-docker-swarm-and-docker-swarmkit?answertab=active#tab-top*






*Source: https://thenewstack.io/kubernetes-vs-docker-swarm-whats-the-difference/*



