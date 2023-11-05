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

### February 2023, Viviane

### August 2023, Cybozu

### October 2023, DMM.com


## 2023: Starting My Master's

### Hexagon

### Multi-node Bare-metal Kubernetes cluster operation

{{% /blocks/section %}}

[github-account]: https://github.com/hanapedia
[GlobeChat]: https://github.com/hanapedia/globe-chat-app
[giikuten-slides]: https://docs.google.com/presentation/d/1O3A96uDKAjjq9dh_T2dx-asjCGYGNNGcSeo_iiU4vvc/edit#slide=id.gf0c778061d_0_49
[MShare-frontend]: https://github.com/yusukey7grizi/mshare_web_app
[MShare-backend]: https://github.com/hanapedia/mshare_serverless_api
[k8s-provisioner]: https://github.com/hanapedia/k8s_provisioner
