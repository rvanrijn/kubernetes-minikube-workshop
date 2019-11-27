# Kubernetes Minikube workshop

Covers the basics of using Kubernetes to manage applications at scale. In this workshop, you'll take an app, build it into a docker container, then use Kubernetes to deploy, scale, and update it.




## Individual Modules

Name | Level| Time Estimate | Completion Status |
------------- | ------------- | ------------ | ------------
[Cluster Bring Up](bring-up) |  Beginner | 1 hour | Ready
[Quickstart](quickstart) |  Beginner | 1 hour | Ready
[Core Kubernetes Concepts](core-concepts) | Beginner | 4 hours | Ready
[Storing State](state) | Intermediate | 2 hours | Ready
[Advanced Concepts](advanced) | Intermediate | 2 hours | Ready
[Spring Cloud](spring-cloud-kubernetes) | Intermediate | 2 hours | Ready


### Cluster Bring Up

* Uses the open source kubernetes release with `cluster/kube-up.sh`
  for cloud bringup
* Option for local docker


### Quickstart

* Quick
* Not complex, uses `kubectl run`, `kubectl expose`.
* Demonstrates the ease of using Kubernetes without learning all the
  concepts and config files up front.


### Core Kubernetes Concepts

* Introduce one concept at a time, and then use that concept
  * Order: pod, service, rc, deployment
* go over a declarative pod representation of quickstart app
  * contains 1 pod
* logs, exec, port forwarding
* introduce service
* overview pods, labels, selectors, and services
* change pod to RC
* discuss RC
* scale pod up
* introduce deployments
* move everything under a deployment
* update to new versions of our app, quick rolling update
  * lightweight here - more detail in "Advanced" module

### Storing State

* Deploy an app with MySQL
* multiple iterations where to store the data, how it goes away
  * start with host volume, end at persistent disk
* More of a lecture module, slides discuss state in greater length

### Advanced Concepts

* Lecture
  * App/container patterns
    http://blog.kubernetes.io/2015/06/the-distributed-system-toolkit-patterns.html
  * mapping non-containerized apps

* Hands on:
  * A/B deployment
  * Canary patterns
  * Rolling Deployments
  * Autoscaling
