<!-- .slide: data-background="#4CA737" -->
## Hello Minikube
###  Guided Exercise Sample

---
<!-- .slide: style="text-align: left;"> -->  
## Introduction

In this exercise, we will begin to explore Kubernetes by installing `Minikube` and `kubectl`, then taking a quick tour of the cluster. 

`Minikube` is a tool allows us to run a single-node Kubernetes cluster locally inside a Virtual Machine(VM). This is useful for familiarizing ourselves with Kubernetes, and as a convenient means for testing applications in a local Kubernetes cluster before deploying to a remote cluster. 


## Instructions

Reminder: All exercises are to be completed in the cloud-based student lab environment. 

1. To install `kubectl` in the lab environment, open a terminal window and follow the [Linux instructions to install kubectl via curl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#tabset-1).

2. Validate kubectl's install with:
    ```
    kubectl
    ```
    You should see the kubectl help menu returned. Note that you won't be able to run kubectl commands at this point, as we have not configured it to communicate with a Kubernetes cluster. Let's do that now!

3. In a new browser tab, open the [Minikube Github page](https://github.com/kubernetes/minikube/releases). Scroll down to the latest **Installation** header, and use the `Linux` `curl` command to install Minikube to your lab environment.

4. Validate Minikube's installation with:

    ```
    minikube
    ```
    Again, you should see minikube's help menu output. 

    Note that although we have installed the Minikube binary, we have **not yet started** the Minikube VM.

5. Start the Minikube VM. **Minikube will take 1-2 minutes to start** in this environment, as it will be starting a VM within a VM. The start time will be shorter on your local laptop.

    ``` 
    minikube start --memory 8192
    ```

    Note that we included the `--memory` argument to tell Minikube that it may use up to 8GB of memory. The default is 1GB.

6. While waiting for Minikube to start, let's look at `kubectl`'s config. It is located at `$HOME/.kube/config`. In a **new terminal window**, view the config file with:

    ```
    cat $HOME/.kube/config
    ```

    Note that this file defines all of the Kubernetes clusters (API endpoints) that `kubectl` may interact with, including any necessary credentials to access those clusters. Together, a cluster-credential combination is known as a `context`. In this case, there is only the `minikube` context. We will use this file later in the course to configure `kubectl` to [access multiple clusters](https://kubernetes.io/docs/tasks/access-application-cluster/configure-access-multiple-clusters/). 

    Close this terminal window, and return to the one where `minikube` is starting. When you see the line `Kubectl is now configured to use the cluster.` and the return of the command prompt, your minikube is ready.


7. Once Minikube has started, run the following commands to validate that `minikube` has started successfully and kubectl has been configured:

   ```
   kubectl get componentstatuses
   ```
   This command provides simple Kubernetes diagnostics and is useful for validating the health of your cluster. You should see a response similar to the following:
   ```
   NAME                 STATUS    MESSAGE              ERROR
   controller-manager   Healthy   ok                   
   scheduler            Healthy   ok                   
   etcd-0               Healthy   {"health": "true"}   
   ```
   We can also check that the single `minikube` node is running:
   ```
   kubectl get nodes
   ```

   You should see output similar to the following, showing a single node called 'minikube':
   ```
   NAME       STATUS    AGE       VERSION
   minikube   Ready     17d       v1.7.5
   ```

8. Internally, `minikube` runs a binary called `localkube` which runs all of the Kubernetes master components together, including Docker so that containers can be run. As a quick exercise, let's examine the internals of minikube.

    Minikube's VM can be accessed with the following command:
    ```
    minikube ssh
    ```
    Once inside, find the `localkube` binary that runs all of the Kubernetes Master components.
    ```
    ps -aux | grep localkube
    ```
    Examine the Docker containers currently inside `Minikube`:
    ```
    docker ps
    ```
    Note the `dashboard`, `kube-dns` and addon containers. We'll look at this shortly. 

    Finally, exit the Minikube shell:
    ```
    exit
    ```

9. Minikube also includes the [Kubernetes Dashboard](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/), a web-based UI for deploying, troubleshooting and managing applications running in your cluster. From the command line, access the dashboard with the following:

     ```
     minikube dashboard &
     ```

    If that command fails, open the following link in a web browser in the lab environment: [http://192.168.99.100:30000/](http://192.168.99.100:30000/).

   If you have some extra time, explore the dashboard. We will begin to learn about all of the pieces you see there shortly!