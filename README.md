# deploy-gitlab-on-minikube

~~~
### Install minikube
https://github.com/kubernetes/minikube/releases


### Add ip to hostfile

Add these entries in your hostfile

~~~
echo $(minikube ip)" gitlab"
echo $(minikube ip)" helloworld.local"
~~~

### Create ingress controller
~~~
kubectl create -f ingress
~~~

### Create internal docker-registry
~~~
kubectl create -f docker-registry
~~~

### Create gitlab server
~~~
kubectl create -f gitlab
~~~

You can create secret with
~~~
kubectl create secret generic gitlab-secret --namespace gitlab --from-file=./gitlab/GITLAB_OMNIBUS_CONFIG --from-file=./gitlab/REGISTRATION_TOKEN
~~~

### Create gitlab runner
~~~
kubectl create -f gitlab-runner
~~~
