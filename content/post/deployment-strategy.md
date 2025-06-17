+++
title = 'Deployment Strategy'
summary = 'Deployment Strategy'
date = 2025-06-14T21:07:55+07:00
draft = false
+++

- [I. Overview](#i-overview)
- [II. Getting Started](#ii-getting-started)
  - [1. Big Bang Deployment](#1-big-bang-deployment)

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

Pros: Simplicity, Speed, Consistency

Cons: High risk, Downtime, Limited Roll Back Option, No Gradual Feedback

**When to use ?**

- Downtime of the application/system is less critical
- New version is fully tested, and there is confidence in its stability
- Small system with fewer dependency
- Or maybe the cost and complexity of a phased rollout is prohibitive