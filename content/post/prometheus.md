+++
title = 'Prometheus'
date = 2026-01-15T14:46:20+07:00
summary = "Refreshing my knowledge of Prometheus."
draft = false
+++

- [I. Overview](#i-overview)
- [II. Prometheus](#ii-prometheus)
  - [Concept](#concept)
  - [Feature](#feature)
  - [Characteristics](#characteristics)

## I. Overview
Prometheus for monitoring.

## II. Prometheus
### Concept
Prometheus is an open-source (OSS) systems monitoring and alerting originally built at SoundCloud and has been joined CNCF in 2016 as the second hosted project.

### Feature
- multi-dimensional data model with time series data
- PromQL to query that data model
- Target are discovered via service discovery or static configuration

### Characteristics
- Pull based system over HTTP
- use push gateway for short-lived task