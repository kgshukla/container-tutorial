# Podman Tutorial
## Lab 1 - Pulling, Running OCI images

Click this [link] (https://learn.openshift.com/subsystems/container-internals-lab-2-0-part-1) to get your lab environment. Click on "Start Session" button to begin your lab. Please follow the instructions on the left hand side of the webpage.

podman cli is similar to docker cli. If you are familiar with docker cli, then using podman is easy. Following commands are used in the lab.

podman pull

podman run

podman ps

podman top 

port mapping 


## Lab 2 - Running pods via Podman
People associate running pods with Kubernetes. And when they run containers in their development runtimes, they do not even think about the role pods could play—even in a localized runtime.  Most people coming from the Docker world of running single containers do not envision the concept of running pods.

Please read this [blog] (https://developers.redhat.com/blog/2019/01/15/podman-managing-containers-pods/) to understand pod concepts. The following commands are taken up from this blog.

Continue running these commands on the same environment that you provisioned in the previous section. If you have lost the environment, click [here] (https://learn.openshift.com/subsystems/container-internals-lab-2-0-part-1) to get an environment.

Run "podman pod" to get a list of all supported attributes

    # podman pod
    
Create a pod

    # podman pod create --name youthful_jones
    
List the pods

    $ podman pod list
    POD ID         NAME             STATUS    CREATED     # OF CONTAINERS   INFRA ID
    9e0a57248aed   youthful_jones  Running 5 seconds ago   1                6074ffd22b93

Note that the container has a single container in it.  The container is the “infra” command. We can further observe this using the podman ps command by passing the command line switch *–pod*.

    $ podman ps -a --pod
    CONTAINER ID  IMAGE                   COMMAND  CREATED      STATUS     PORTS  NAMES               POD
    6074ffd22b93  k8s.gcr.io/pause:3.1    3 minutes ago  Up 3 minutes ago         9e0a57248aed-infra  9e0a57248aed

Add a container to the pod

    $ podman run -dt --pod youthful_jones docker.io/library/alpine:latest top
    0f62e6dcdfdbf3921a7d73353582fa56a545502c89f0dfcb8736ce7be61c9271
    
And now two containers exist in our pod

    $ podman pod ps
    POD ID         NAME            STATUS  CREATED         # OF CONTAINERS   INFRA ID
    9e0a57248aed   youthful_jones  Running 7 minutes ago   2                 6074ffd22b93
    
Looking at the list of containers, we also see each container and their respective pod assignment.

    

    $ podman ps -a --pod
    CONTAINER ID  IMAGE                            COMMAND  CREATED         STATUS             PORTS  NAMES               POD
    0f62e6dcdfdb  docker.io/library/alpine:latest  top      14 seconds ago  Up 14 seconds ago         awesome_archimedes  9e0a57248aed
    6074ffd22b93  k8s.gcr.io/pause:3.1                      7 minutes ago   Up 7 minutes ago          9e0a57248aed-infra  9e0a57248aed


If you would like to know more on podman pod, please refer to this blog which explains more on the topic


https://developers.redhat.com/blog/2019/01/15/podman-managing-containers-pods/
