# Workload-Aware AI Access and Consumption Governance

* Authors: @divyaan23
* Status: Proposed

# What?

Define common semantics for governing which AI providers and models a
Kubernetes workload is authorized to consume at runtime, and for attributing
and constraining AI consumption at the workload level.

# Why?

### AI authorization goes beyond network access

A workload's ability to reach an AI service does not necessarily mean that
the workload should be authorized to consume every model exposed by that
service.

AI workloads need authorization decisions that can distinguish the workload
making the request, the AI provider or service being accessed, and the model
or model class being consumed.

### AI authorization happens at runtime

Provider or model selection can occur after a workload has been admitted and
may change throughout the workload's lifetime without any change to its
Kubernetes configuration.

AI authorization therefore needs to remain applicable when AI requests are
processed at runtime, rather than being limited to workload admission.

### AI consumption needs workload context

Request counts alone do not describe AI consumption. AI requests to the same
service can consume substantially different amounts of resources, with token
usage being a common example.

Platform administrators need a consistent way to attribute AI consumption to
the responsible Kubernetes workload and express consumption constraints such
as rates, allocations, or budgets.

## Definitions

* **Workload-Aware AI Governance**: Authorization and consumption-governance
  decisions that relate a Kubernetes workload to the AI provider, model, and
  consumption associated with its runtime AI requests.

## User Stories

* As a platform administrator, I want to identify the Kubernetes workload
  responsible for an AI request so that authorization and consumption can be
  evaluated in workload context.

* As a platform administrator, I want to define which AI providers or services
  a workload may access so that workloads cannot consume services outside
  their permitted scope.

* As a platform administrator, I want to define which models a workload may
  consume independently of provider-level network access because a provider
  may expose models with different organizational policies.

* As a platform administrator, I want AI authorization to remain applicable
  to runtime requests so that workloads remain governed when provider or model
  selection occurs after workload admission.

* As a platform administrator, I want AI consumption to be attributable to
  workloads and governed through rate, allocation, or budget constraints so
  that shared AI resources can be managed consistently.

## Goals

* Define common semantics for workload-to-provider authorization.
* Define common semantics for workload-to-model authorization.
* Define common semantics for attributing AI consumption to Kubernetes
  workloads.
* Support workload-level consumption constraints such as rates, allocations,
  or budgets.
* Enable policy intent to remain portable across compatible AI gateway
  implementations.

## Non-Goals

This proposal does not initially define:

* Kubernetes APIs or policy resources.
* Gateway implementation or enforcement mechanisms.
* Egress, routing, or inference scheduling.
* Payload processing or AI safety mechanisms.
* Provider-specific token counting.
* Provider pricing, billing, chargeback, or cost-allocation systems.

# How?

# Relevant Links

* [Slack Discussion](https://kubernetes.slack.com/archives/C09EJTE0LV9/p1791975897834239)