+++
title = 'Docker'
summary = 'What is Docker ?'
date = 2025-06-14T21:07:55+07:00
draft = false
+++

- [I. Overview](#i-overview)
- [II. Getting Started](#ii-getting-started)
  - [The Docker revolution](#the-docker-revolution)
    - [Physical Server](#physical-server)
    - [Virtual Server](#virtual-server)
    - [Container](#container)

## I. Overview
In this post, I will sumarize the defintion of docker and the revolution of docker. All knownledge of this article is come from the book name 'Docker Deep Dive' by Nigel Poulton

## II. Getting Started

![targets](/img/tech/docker-revolution.png)

### The Docker revolution
#### Physical Server
Application are the  powerhouse of every modern business, then when application break, business break.

But in the past, it limited to running one application per server. Every time a business needed a new application, it had to buy a new server. And it also can lead to under utilize of resource of server. This was a waste of company capital and environmental resources.

#### Virtual Server
Then VMWare has come, and gave the world a gift - the Virtual Machine - a technology that allowed us to run multiple business applications on a single server safely.

Business now could run new applications on an existing server, spawning a golden age of maximizing the value of existing assets.

But VMs also have disadvantage, for example, every VM needs its own dedicated operating system. Unfortunately, this has serveral drawbacks, including
- VM are slow to boot and not very portable
- VM have fixed allocation of CPU/RAM/Disk space
- reduce perfomance because of hypervisor

#### Container
While most of us were reaping the benefit of VMs, web scalers like Google had already moved on from VMs and were using containers.

A feature of the container model is that every container shares the OS of the host it's running on. This mean a single host can run more container than VMs. Container are also faster and more portable than VMs.

===> TBD