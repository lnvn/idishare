+++
title = 'Deployment Strategy'
summary = 'Deployment Strategy'
date = 2025-06-14T21:07:55+07:00
draft = false
+++

- [I. Overview](#i-overview)
- [II. Getting Started](#ii-getting-started)
  - [1. Big Bang Deployment](#1-big-bang-deployment)
  - [2. Rolling Deployment](#2-rolling-deployment)
  - [3. Blue Green Deployment](#3-blue-green-deployment)

## I. Overview
Deployment Strategy

## II. Getting Started
Top 5 most-used deployment strategies
- Big Bang Deployment
- Rolling Deployment
- Blue-Green Deployment
- Canary Deployment
- Feature Toggle

### 1. Big Bang Deployment
![targets](/img/tech/big-bang-deployment.png)

**Defintion:** The Big Bang deployment strategy is a method of deploying new application or system version where the entire update is rolled out in a single step to all user at once. This strategy involves switching from the old system to the new one simultaneously, effectively making the update live everywhere at the same time.

**Process:**

1. Pre-Deployment
   - Prepare the new version in a staging/test environment
   - Ensure all component are tested and ready for release

2. Deployment
   - The old version of the application/system is stopped/disabled
   - The new version is deployed and made live across all environments

3. Post-Deployment
   - Monitor system

**Pros and Cons:**

   - Pros: Simplicity, Speed, Consistency
   - Cons: High risk, Downtime, Limited Roll Back Option, No Gradual Feedback

**When to use ?**

   - Downtime of the application/system is less critical
   - New version is fully tested, and there is confidence in its stability
   - Small system with fewer dependency
   - Or maybe the cost and complexity of a phased rollout is prohibitive

### 2. Rolling Deployment
![targets](/img/tech/rolling-deployment.png)

**Definition:** Rolling deployment is a deployment strategy used in software development to update an application gradually without downtime. In this approach, new instances of application are incrementally deployed while old ones are taken offline. This ensure continuous availability of service to end user.

**Process:**

1. Pre-Deployment
   - Build and test the new version in a staging environment.
   - Configure rollout strategy and health checks.

2. Deployment
   - Gradually replace old instances with the new version in small batches.
   - Validate each batch using health checks and monitoring tools.

3. Post-Deployment
   - Ensure all instances are running the new version.
   - Monitor system performance.

**Pros and Cons:**

   - Pros: No Downtime, Minimized Risk, Continuous Delivery
   - Cons: Complexity, Version Mismatch, Longer Deployment Time

**When to use ?**
   - The system cannot afford downtime (e.g., e-commerce, banking, or SaaS applications)
   - You want to test the new version incrementally and reduce the risk of system-wide failure
   - The new release includes minor updates or non-breaking changes to the application
   - The system does not have sufficient resources to deploy two full environments
   - The old and new versions can coexist without causing conflicts (e.g., API or data schema compatibility)
   - Works well with containerized and microservices-based applications in environments like Kubernetes, ECS, or similar orchestration platforms

### 3. Blue Green Deployment
![targets](/img/tech/blue-green-deployment.png)