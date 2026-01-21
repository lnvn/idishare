+++
title = 'N Tier Architecture'
date = 2026-01-21T17:46:03+07:00
summary = "Refreshing my knowledge of n-tier architecture"
draft = false
+++

- [I. Overview](#i-overview)
- [II. Definition](#ii-definition)

## I. Overview
Building an n-tier layered architecture

## II. Definition
**Definition**:
- In n-tier architecture (aka multitier architecture) we need to apply principle of loosely coupled design and attributes of scalability and elasticity.
- We divide product function into multiple layers such as:
  - presentation
  - business
  - service
- so that each layer can be implemented and scaled independently.

**Feature**:
- Provide flexibility to add new feature in each layer without disturbing features of other layers.
- Keep each layer secure and isolate from others, so if one layer gets compromised, the other layers won't be impacted.
- Application troubleshooting and management also become manageable because we can quickly pinpoint where the issue is coming from and which part of the application needs to troubleshoot.