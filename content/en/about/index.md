---
title: About Hanapedia
linkTitle: About
menu: {main: {weight: 10}}
---

{{% blocks/cover title="About Me" image_anchor="bottom" height="auto" %}}

{.mt-5}
Information Science Master's student in Tokyo, researching microservice and autonomous root cause analysis method.

{{% /blocks/cover %}}


{{% blocks/section color="light" type="row" %}}

{{% blocks/feature icon="fa-brands fa-golang" title="Languages" %}}
Golang, YAML, HCL, C, Python, Typescript, Rust, eBPF
{{% /blocks/feature %}}


{{% blocks/feature icon="fab fa-github" title="My GitHub!" %}}
You can find all of my projects on my [GitHub Account](https://github.com/hanapedia) !
{{% /blocks/feature %}}


{{% blocks/feature icon="fa-solid fa-network-wired" title="Areas of Interest" %}}
Networking, Observability, Microservices
{{% /blocks/feature %}}
{{% /blocks/section %}}


{{% blocks/section color="primary" %}}
# Software Engineering Background
## 2019: Hello World, Hello Programming
I encoutered programming in 2019 when I took programming course in college.
Since then, I was entrigued by the cources in Inforamtion Science and continued to learn the basics of topics such as OS, Networking, Machine Learning/Deep Learning, Algorithm & Data Structure.

<br>
<br>

## 2021: Jumping into the world of Web
Although I was enjoying academic programming used in college courses, I had always wondered where programming is used in the actual world. That was the starting point of my jouney in the web.

<br>

### August 2021, My First Major Project: [GlobeChat][]
First, I started from Frontend and Backend development using Laravel and Vue.
I developed a group chatting application called GlobeChat, which has 3D UI that visualize the engagement from the users in the chat room. 
I also [presented][giikuten-slides] this application in a student pitch contest in Japan called Giikuten. 

{{% imgproc globechat.gif Fill "640x360" %}}
GlobeChat in Action.
{{% /imgproc %}}

The whole application was developed and deployed in the spand of *2 months*.
##### **Tech Stack**
Frontend: Vue, Three.js

Backend: Laravel

<br>

### December 2021, My First Team Development: MShare
As a team of four, we have developed Video Sharing Web Application that provides a unique rating system. User's facial expressions when watching the video are tallied directly to the rating of the video.
{{% imgproc mshare Fill "640x640" %}}
MShare in Action.
{{% /imgproc %}}

I worked on the integration of the facial expression detector on to the frontend and also the deployment of the backend to AWS services.

The original application was developed in a week for a Hackason and was later refined.
##### **Tech Stack**
[Frontend][MShare-frontend]: Next.js, React

[Backend][MShare-backend]: Next.js, AWS API Gateway, AWS Lambda

<br>
<br>

## 2022: Diving Deeper
As I continued my jouney in the web development, I became more and more interested in lower layers of the web.
At the same time, I was wondering how bigger applications are developed and ran in the real world.
That was when I started look into concepts such as Kubernetes and Microservices.

### April 2022 ~ February 2023, Senior Thesis
After learning about the tradeoffs of microservice architecture, I decided that I wanted to focus on the tradeoff between developer efficiency and operational efficiency of microservice.

Specifically, I analyzed the effect of logical network of microservice on the performance of autonomous root cause analysis.

Also, I learned from development of experiment infrastructure and tools.

#### Bare-metal Kubernetes Cluster
One of the development experience that I gained from working on senior thesis was the initialization and operation of Bare-metal Kubernetes cluster.

##### Internals
The Kubernetes cluster was constructed on top of multiple KVMs on a single physical machine.
The KVMs were managed using Terraform and the initialization of the Kubernetes cluster was done by Ansible.

{{% imgproc first-cluster Fill "640x360" %}}
Image of the cluster.
{{% /imgproc %}}

This [project][k8s-provisioner] was later reimplemented for initializing Kubernetes cluster on multiple Bare-metal nodes.

<br>

#### Microservices Topology Configuration tool (prototype)
One of demand that I had during my senior thesis is that I wanted to be able to generate benchmark microservice application of various logical network topology.
For this, I have developed a tool to generate microservice application that has various height and weight for logical network topology. 

##### Internals
I used Jinja2 template to generate Go code for request handler of a microservice to generate the desired logical network topology.

However, this approach had limited scalability as I had to build the docker image for each services every time I configure them. This limitation was later reworked during master's.

<br>
<br>

## 2023: Starting My Career as Software Engineer
After completing my senior thesis, I started looking for software engineering job.

### February 2023, Viviane
First internship that I got was in a startup company named [Vivian][].
I was employed as a fullstack developer working on frontend, backend, and infrastructure.

### August 2023, Cybozu
Another internship that I had was with [Cybozu][], which is a company that provides a BtoB SaaS.
I was employed for three weeks course where I worked on improving the container registy in a large-scale Kubernetes cluster.
More specifically, I've completed the following during the internship.
- I tested an OSS container registry named [spegel][], a new type of container registry cache that is designed to share the local cache on each node.
- I developed a kubernetes custom controller for delaying the pod scheduling to enhance the benefit of using spegel.

The work that I've dones is documented as a [blog][cybozu-blog] in Japanese.

### October 2023, DMM.com
Another internship that I participated in was with [DMM.com][DMM]. I was employed for 5 weeks in a SRE team in Microservices Architect group.
During the internship, I was assigned series of operational tasks for multi-cloud kubernetes cluster.
More specifically, I updated version of three tools running in the cluster, fixed 4 different instances of error messages recorded by Datadog Agent, and added a new CI workflow for configuring IAM role in AWS.

## 2023: Starting My Master's
I started working on my master's research along side working my internships.

I already had decided to continue on with my senior thesis in master's and dive further into analyzing how  different types of network communication affect the accuracy of the root cause analysis.
For this, I had to improve the tools that I created during my senior thesis.

### Multi-node Bare-metal Kubernetes cluster operation
As for the Ansible project for provisioning bare-metal kubernetes cluster, I had to improve it so that I can create Kubernetes cluster on top of KVMs on multiple physical machines.
This was a needed change because I noticed that I needed more computing power for my experiments.

Also, because the cluster need to run continuously, I have improved the operation of the cluster. In particular, I introduced to GitOps to manage the installations of cluster tools such as monitoring infrastructure and service mesh.

- [Improved Ansible][lab-cluster].
- [The GitOps project][lab-cluster-app].

### Hexagon
As for the microservice topology configuration tool, I had to do a major rework so that I could incorporate some degree of application logic such as how each endpoint on a microservice will invoke endpoints on other microservices.

Also, I had to improve the tooling so that I can have more variation for types of communication used by the microservices.

With new requirements considered, I have developed [Hexagon][], a microservice benchmark generation tool which can configure the following on each microservice.
1. Exposed API
    - each microservice can expose APIs such as REST, gRPC, Kafka consumer
    - each API can have configurable number of endpoints such as routes and topics.
2. API Invocation
    - each endpoints on exposed API can have handlers that invoke endpoints on other microservices in configurable order or asynchronously.
    - in addition to the exposed API types, handlers can also invoke DB endpoints such as Mongo collection and Redis cache.
This configurability allows the developer/researcher to generate microservices benchmark with various network topology and communication patterns.


{{% /blocks/section %}}

[github-account]: https://github.com/hanapedia
[GlobeChat]: https://github.com/hanapedia/globe-chat-app
[giikuten-slides]: https://docs.google.com/presentation/d/1O3A96uDKAjjq9dh_T2dx-asjCGYGNNGcSeo_iiU4vvc/edit#slide=id.gf0c778061d_0_49
[MShare-frontend]: https://github.com/yusukey7grizi/mshare_web_app
[MShare-backend]: https://github.com/hanapedia/mshare_serverless_api
[k8s-provisioner]: https://github.com/hanapedia/k8s_provisioner
[Vivian]: https://viviane.jp/
[Cybozu]: https://cybozu.co.jp/
[spegel]: https://github.com/XenitAB/spegel
[cybozu-blog]: https://blog.cybozu.io/entry/2023/09/21/161930
[DMM]: https://dmm-corp.com/
[lab-cluster]: https://github.com/hanapedia/lab-cluster
[lab-cluster-app]: https://github.com/hanapedia/lab-cluster-app
[Hexagon]: https://github.com/hanapedia/hexagon
