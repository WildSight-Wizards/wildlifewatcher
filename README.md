I. Overview
II. Vision
III. Goals and Opportunities
  Immediate Business Goals
  Long Term Business Goals
  Business Opportunity
  Competitors
IV. Use Cases
  Customer Journey
  Case 1. Customer orders via PoS
  Case 2. Customer orders online
  Maintenance and Failure Operations
V. Requirements
  Prioritized Architecture Characteristics
    1. Enable Discovery - Agility
    2. Affordable DevSecOps - Viability
    3. Easy to Pivot - Flexibility
    4. Availability
    5. Security
    6. Scalability
    7. Performance
  Design Constraints
VI. High-Level Architecture
  Web/Mobile Experience
  Offline Strategy for Smart Fridges
VII. Selected Topics of Mid-Level Architecture
  Scheduling System
  The Missing Data Tier
  How we Avoid Firebase Lock-in 
  Lean on Data
  ChefTec Integration
VIII. Milestones
  Milestone 1. Marketing and Analytics
  Milestone 2. Mobile App Menu
  Milestone 3. Mobile App Orders
  Milestone 4. Web Orders
  Milestone 5. Customer Profiles
  Milestone 6. Multi-Location and Scaling Delivery
IX. ADRs
  ADR 1. Use of API
  ADR 2. Use of healthcheck pattern
  ADR 3. Use of API Gateway
  ADR 4. Use of Application Gateway
  ADR 5. Use of keyvault
  ADR 6. Use of cognitive services
  ADR 7. Newsletters and Client Communication
  ADR 8. Smart Fridge Access will be Controlled Both on Prem and via CDN
  ADR 9. Google Firebase will be used as Presentation Layer


# Overview

Wildlife AI is a charitable trust using AI for wildlife conservation. Wildlife.ai work with grassroots wildlife conservation projects and develop open-source solutions using machine learning. They also 
organise community events, seminars and educational activities to build and maintain machine learning solutions to reduce the current rate of species extinction.

# Assumptions

* Only deployed in one region
* Only mobile client (so no BFF pattern to use or clients competing with different requirements)
* No analytics functionality required (i.e. Azure Data Explorer)
* Data is not stored in the cloud, regarding wildlife sightings.

# Use Cases

* Upload to platforms
* View device information
* Analyse frames

# Risks

* Lack of expertise.
* Affordability of monitoring
* Deployability to a poor-network issue.

# Priotized Architecture Characteristics

## Deployability
Wildlife.AI will potentially deploy to hundreds, if not thousands, of cameras in the wild where network connectivity may be poor. Thus, any deployment to cameras, be it code or models, must be quick and easy. We would like to avoid issues where a camera in the middle of a deployment goes offline and have different code versions across the fleet of cameras.

## Affordability
Wildlife.ai are a charity and thus any solution envisaged must be affordable and without costly third party licenses. The solution must avoid the use of expensive third-party solutions and use Azure native services as much as possible, although this may risk cloud vendor lock-in.

## Fault Tolerance
Given the harsh environment wildlife.ai operate in, the application must be able to endure and withstand any faults, e.g. if a camera is damaged, which is possible.

## Availability
The application must be available at all times. This is crucial to ensurte that all relevant wildsight sightings are captured by the camera and subsequently uploaded.

## Privacy

## Performance
Videos need to be uploaded in real-time, so performance is critical. In addition, cameras won't have the hardware to run complex code, so the code must be lightweight and optimised where possible.

## Recoverability
When an application error is encountered, recovery needs to be as fast as possible. It won't be desirable if the application is inoperable and wildlife sightings go by, unnoticed.

# Requirements

# Design Constraints

Lack of APIs on third party systems

# Architecture

# Threat Modelling

# Risk Storming

# Architectural Decision Records