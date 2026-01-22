+++
title = 'N Tier Architecture'
date = 2026-01-21T17:46:03+07:00
summary = "Refreshing my knowledge of n-tier architecture"
draft = false
+++

- [I. Overview](#i-overview)
- [II. Definition](#ii-definition)
- [III. Example](#iii-example)
  - [1. The web layer](#1-the-web-layer)
  - [2. The application layer](#2-the-application-layer)
  - [3. The database layer](#3-the-database-layer)

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

## III. Example
The most famous architecture in multilayer design is three-tier architecture
- **Web layer**: is the user-facing part of the application.
- **Application layer**: contain business logic and acts upon information received from the web layer
- **Database layer**: data stored

### 1. The web layer
The web layer aka the presentation tier, it provides an user interface that help the end user to interact with the application. For example: web page.

This tier collects the information from the users and passes it to the application layer.

### 2. The application layer
The application layer aka the logic tier, it is the core of the product where all the business logic resides.

Application layer processes the user input to perform business logic such as count of orders, sum of amounts ... and then return information to the web layer to render it for the user.

### 3. The database layer
The database layer aka the data tier, store all the information related to user profiles and transactions. it contains any data that needs to persist in being stored in the data tier. This information is sent back to the application layer for logic processing and then renders to the user in the web layer.

