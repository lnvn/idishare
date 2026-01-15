+++
title = 'Prometheus'
date = 2026-01-15T14:46:20+07:00
summary = "Refreshing my knowledge of Prometheus."
draft = false
+++

- [I. Overview](#i-overview)
- [II. Concept](#ii-concept)
  - [1. Concept](#1-concept)
    - [a. Data Model](#a-data-model)
    - [b. Metric Types](#b-metric-types)
  - [2. Feature](#2-feature)
  - [3. Characteristics](#3-characteristics)
- [III. Architecture](#iii-architecture)
  - [1. Components \& Architectture](#1-components--architectture)

## I. Overview
Prometheus for monitoring.

## II. Concept
### 1. Concept
Prometheus is an open-source (OSS) systems monitoring and alerting originally built at SoundCloud and has been joined CNCF in 2016 as the second hosted project.

#### a. Data Model
Prometheus fundamentally stores all data as time series, which is a streams of timestamped values belonging to the same metric and the same set of labeled dimensions.

Prometheus may also generate temporary derived time series as the result of queries.

**Metric names and labels**
Every time series is uniquely identified by its metrics name and optional key-value pairs called labels.

**Metric names**
- Metric names should specify the general feature of a system that is mesured
- Metric names may use any utf-8 characters

**Metric labels**
- Label let us capture different instances of the same metric name

**Notation**
```
<metric name>{<label name>="<label value>", ...}
```

#### b. Metric Types
The prometheus client libraries offer 4 core metrics types:
- Counter
- Gauge
- Histogram
- Summary

**Counter**
A counter is a metrics that represents a single increasing counter whose value can only increase or be reset to zero on restart (E.g. requests served, tasks completed ...)

Do not use counter to expose a value that can decrease. (E.g. Currently running processes) Instead use a gauge.

**Gauge**
A gauge is a metric that represents a single numerical value that can arbitrarily go up and down.

Gauges are typically used for measured values like temperatures or current memory usage, number of concurrent request.


### 2. Feature
- multi-dimensional data model with time series data
- PromQL to query that data model
- Target are discovered via service discovery or static configuration

### 3. Characteristics
- Pull based system over HTTP
- use push gateway for short-lived jobs

## III. Architecture
### 1. Components & Architectture
- Prometheus Server (1) scrapes data via retrieval and stores into storage
- Client libraries for instrumenting application code
- A Push Gateway (2) for supporting short-lived jobs
- Special-purpose exporters (3) for special service
- Alert Manager (4) to handle alert
- And other support tools

![targets](/img/tech/prometheus-architect.png)