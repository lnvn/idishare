+++
title = 'Design for Least Privilege'
summary = 'Principle of least privilege'
date = 2025-07-10T11:02:06+07:00
draft = false
+++

- [I. Overview](#i-overview)
- [II. Getting Started](#ii-getting-started)
  - [Least Privilege](#least-privilege)
  - [Zero Trust Networking](#zero-trust-networking)
- [Reference](#reference)

## I. Overview

"Because we can't rely on human perfection, we must assume that any possible bad action or outcome can happen. Therefore, we recommend designing the system to minimize or eliminate the impact of these bad actions"

## II. Getting Started

<!-- ![targets](/img/tech/gitflow-high-level.png) -->
### Least Privilege
The principle of least privilege refers to an information security concept in which a user is given the minimum level of access - or permissions - needed to perform their job functions. One of a best practice is "Deny by default".

The model can by applied to applications, systems or connected devices that require privileges or permissions to perform a required task. Effective least privilege enforment requires a way to centrally manage and secure privileged credentials.

### Zero Trust Networking
The notion that a user's network location (begin within the company's network) doesn't grant any privileged access. For example, plugging into a network port in a conference room does not grant more access than connecting from elsewhere on the internet. Instead, a system grants access based on a combination of user credentials and device credentials - what we know about the user and what we know about the device 

## Reference
- [Building Secure and Reliable Systems](https://google.github.io/building-secure-and-reliable-systems/raw/ch05.html)