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
  - [4. Canary Deployment](#4-canary-deployment)

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

**Definition:** Blue-green deployment is a deployment strategy that reduces downtime and risk by running two identical production environments, referred to as "Blue" and "Green". At any given time, only one of the environments is live and serving production traffic. For example, if Blue is live, the next version of the application is deployed to the Green environment. Once the new version is ready, traffic is switched from Blue to Green, making Green the new live environment.

**Process:**

1. Pre-Deployment
   - The current version of the application is running in the live environment (e.g., Blue)
   - A complete, identical environment (Green) is created
   - The new version of the application is fully deployed to the Green environment

2. Deployment
   - The Green environment is thoroughly tested to ensure it is working correctly (e.g., integration tests, smoke tests)
   - The router or load balancer is reconfigured to switch all incoming traffic from the Blue environment to the Green environment. This cutover is typically instantaneous

3. Post-Deployment
   - The Blue environment is kept on standby for immediate rollback if issues are discovered in the Green environment.
   - The Blue environment can be decommissioned or used as the staging area for the next release.

**Pros and Cons:**

   - Pros: Instant Rollback, No Version Mismatch, Simplified Testing.
   - Cons: Higher Cost, Database Compatibility Challenges, Abrupt Traffic Switch.

**When to use ?**
   - The system requires zero downtime and the ability for instant, simple rollbacks.
   - The infrastructure costs of maintaining two identical production environments are acceptable.
   - You want to avoid the complexity of having different versions of the application code running simultaneously.
   - You need to conduct extensive testing (including load tests) on the new version in a production-identical environment before it receives any live traffic.
   - Changes between versions are self-contained and do not have complex, breaking database schema dependencies.
   - Works well with immutable infrastructure where environments can be easily created and destroyed.

### 4. Canary Deployment
![targets](/img/tech/canary-deployment.png)

**Fun Fact:**
   - The name "canary deployment" comes from the old mining practice of using a "canary in a coal mine"
   - Miners would bring a caged canary down into the mines with them. Canaries are much more sensitive to toxic gases (like carbon monoxide) than humans. If the canary showed signs of distress or died, it was an early warning for the miners to evacuate immediately before they were affected

![targets](/img/tech/canary-in-the-coal-mine.jpg)

**Definition:** Canary deployment is a strategy where a new version of an application is gradually rolled out to a small subset of users or servers before making it available to the entire user base. This small group acts as a "canary in a coal mine," allowing teams to test the new version in a real production environment with minimal impact. If the new version performs as expected, the rollout is progressively expanded.

**Process:**

1. Pre-Deployment
   - Build and test the new version in a staging environment
   - Define the initial user subset (the "canary" group) and key performance metrics for success (e.g., error rate, latency, resource utilization)
   - Prepare the production environment to run both the old and new versions side-by-side

2. Deployment
   - Route a small percentage of live user traffic (e.g., 5%) to the new version (the canary). The rest of the traffic continues to go to the stable, old version
   - Closely monitor the canary group against the predefined metrics. Compare its performance to the stable version
   - If the canary is healthy, gradually increase the percentage of traffic routed to the new version. If issues arise, immediately roll back by directing all traffic back to the old version

3. Post-Deployment
   - Once 100% of the traffic is successfully routed to the new version, the old version instances can be decommissioned
   - Continue monitoring the system to ensure long-term stability

**Pros and Cons:**

   - Pros: Safest Deployment (minimal blast radius), Real-World Testing, Zero Downtime
   - Cons: Highest Complexity, Requires Advanced Monitoring, Slower Rollout

**When to use?**

   - The release contains high-risk or experimental features that need validation with real user traffic
   - You want to gather performance data and user feedback before committing to a full rollout
   - The system has robust monitoring, feature flagging, and traffic-shaping capabilities
   - You want to perform A/B testing by directing different user segments to different versions
   - Suitable for large-scale applications where even a small percentage of traffic provides a statistically significant sample for testing