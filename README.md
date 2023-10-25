

V. Prioritized Architecture Characteristics
    1. Deployability
    2. Affordability
    3. Fault Tolerance
    4. Availability
    5. Privacy
    6. Scalability
    7. Performance
VI. Requirements
VII. Design Constraints
VIII. High-Level Architecture
IX. Selected Topics of Mid-Level Architecture
  Limp=-home mode
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

# Tech Choices

![Polly Logo](<1 dqHU0u0G8EXYFFRc-S0NuA.jpg>)

![dotnet core logo](NET_Core_Logo.svg.png)

# Assumptions

* Only deployed in one region
* Only mobile client (so no BFF pattern to use or clients competing with different requirements)
* No analytics functionality required (i.e. Azure Data Explorer)
* Data is not stored in the cloud, regarding wildlife sightings (i.e. uploaded straight to third party services)
* Wildlife.ai have basic tech skills (in the major cloud providers) to support a solution. No experience with third party providers for monitoring etc.

# Use Cases

* Upload to platforms
* View device information
* Analyse frames

# Risks

* Lack of expertise.
* Affordability of monitoring
* Deployability to a poor-network issue.
* Lack of control (or a "limp-home" mode) with regards to third party service dependencies
* The exclusive use of Azure, while promoting cohesion and cost-effectiveness, does also present a risk of vendor lock in.

# Priotized Architecture Characteristics

## Deployability
Wildlife.AI will potentially deploy to hundreds, if not thousands, of cameras in the wild where network connectivity may be poor. Thus, any deployment to cameras, be it code or models, must be quick and easy. We would like to avoid issues where a camera in the middle of a deployment goes offline and have different code versions across the fleet of cameras.

## Affordability
Wildlife.ai are a charity and thus any solution envisaged must be affordable and without costly third party licenses. The solution must avoid the use of expensive third-party solutions and use Azure native services as much as possible, although this may risk cloud vendor lock-in.

## Fault Tolerance
Given the harsh environment wildlife.ai operate in, the application must be able to endure and withstand any faults, e.g. if a camera is damaged, which is possible.

## Availability
The application must be available at all times. This is crucial to ensurte that all relevant wildsight sightings are captured by the camera and subsequently uploaded, and so that the application captures a wholely accurate state of the environment it is in, to aid research.

## Privacy
Anytime the use of AI is involved, privacy (and by extension, ethics) are key considerations. This is to ensure the data captured is not breached and used by adverse actors, such as animal hunters/poachers - which goes against the entire mission of Wildlife.AI.

## Performance
Videos need to be uploaded in real-time, so performance is critical. In addition, cameras won't have the hardware to run complex code, so the code must be lightweight and optimised where possible.

## Recoverability
When an application error is encountered, recovery needs to be as fast as possible. It won't be desirable if the application is inoperable and wildlife sightings go by, unnoticed.

# Requirements

## REQ-001 - Users should be able to communicate with the camera using a mobile app (to set the
cameras on/off and adjust settings without opening the cameras) <br />
## REQ-002 - Users should be able to analyse the videos using common camera trap labelling platforms
(Wildlife Insights, TrapTagger or Trapper) <br />
## REQ-003 - Users should be able to publish frames from the videos to iNaturalist for experts to help with
the identification of the species <br />
## REQ-004 Users should be able to easily train edge models. using their own labelled videos, and
upload the models to the cameras (using third party services like Roboflow, Edge Impulse or
TensorFlow Lite) <br />
## REQ-005 Users should be able to publish the species occurrences to GBIF the Camtrap DP, data
exchange format <br />
## REQ-006 Cameras should be able to process the footage on the device and send a small alert
message to the users via LoraWan, 3G or satellite. <br />


## A map function will need to display all the locations with cameras installed in the region

# Architecture Principles

## Camera models and code must be very concise and quick and easy to deploy

## In addition, cameras should be tamper-proof.
To abide by defence in depth

# Effective architecture characteristics

| ID            | Characteristic | 	Applicable to | Source |
| -----------   | -----------    |----------------|--------|
| Header        | Privacy        | API, Camera    | REQ-001|
| Paragraph     | Deployability  | Camera         | REQ-008|
| Affordability | 




# Design Constraints

Lack of APIs on third party systems

# Architecture

# Threat Model

# Risk Storming

![Risk Model](image.png)

# Architectural Decision Records

## Use of API
## Use of healthcheck pattern
## Use of API Gateway
## Use of Application Gateway
## Use of keyvault
## Use of cognitive services
