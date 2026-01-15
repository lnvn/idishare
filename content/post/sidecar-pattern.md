---
title: 'Sidecar Pattern'
summary: 'What is Sidecar pattern, and what is it using for?'
date: 2025-11-26T20:00:31+07:00
draft: false
---

- [I. Overview](#i-overview)
- [II. Getting Started](#ii-getting-started)

## I. Overview
This post describe the sidecar pattern and some use case of it

## II. Getting Started

**Definition:** The sidecar Pattern involves deploying a helper container/process alongside a main application container/process. This "sidecar" is responsible for handling auxiliary task that the main application needs but are not part of its core business logic.

![targets](/img/tech/sidecar-picture.png)

Imagine your main application is a motorcycle. Its purpose is specific and well-defined: to drive. It's optimized for that one job. Now, you want to add extra functionality, like carrying luggage or a passenger. Instead of re-engineering the entire motorcycle, you attach a sidecar

  - Motorcycle (Main Application): Does the core work. It doesn't know or care what is in the sidecar.
  - Sidecar (Sidecar Process): Provides supporting features. It runs alongside the motorcycle, shares the same journey (lifecycle), but encapsulates its own logic.
  - The Attachment: Both share the same context (like the network and storage).

**Why use it ?**

The primary goal is to decouple cross-cutting concerns from the main application code. These are task that many services need but aren't part of their specific job, such as:
  - Logging: main application write logs, and sidecar collects, formats, and forwards them to a centralized logging system
  - Monitoring & Metrics: a sidecar can collect performance metrics from the application and export them to a monitoring system
  - Configuration management: a sidecar can pull configuration updates from a central store (Git, Vault, ...) and make them available to the main application on a shared volume.
  - Service Mesh Proxy

**Some Diagram**

---
![targets](/img/tech/logging-sidecar.png)

---
![targets](/img/tech/git-sync-sidecar.png)

---
**Pros and Cons**

Pros: Language Independence, Reduces Complexity in Application Code, Reusability, Encapsulation

Cons: Increased Complexity in Deployment, Resource Overhead, Potential for Latency

**Summary:** The Sidecar pattern is about separating concerns. While it's an almost essential tool for managing the distributed complexity of a microservices architecture, its principle of decoupling is useful anytime you want to add functionality to an application without modifying its core code.