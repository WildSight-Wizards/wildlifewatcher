# Requirements Overview

Wildlife AI is a charitable trust using AI for wildlife conservation. Wildlife.ai work with grassroots wildlife conservation projects and develop open-source solutions using machine learning. They also 
organise community events, seminars and educational activities to build and maintain machine learning solutions to reduce the current rate of species extinction.

# Assumptions

* We assume that a thorough vetting process is applied for accepting users onto the platform to ensure, as much as possible, that information regarding animals location and numbers are not made available to animal poachers and other such criminal organisations. We expect this facility to be in place as it will be very difficult for the application to ensure the user's genuine reasons for requesting such information.
* Start with a mobile client and a web application. Same responsive and adaptive application (BFFs might be used in the future)
* Observability using Cloud native solutions at the beginning. No particular reporting needs but the solution should accommodate such requirements in the future.
* Wildlife.ai users are allowed to buy a camera and install it wherever they consider appropriate, to spot specific wildlife

# Considerations

* Cameras will have to have the ability of connecting to a message broker using IoT protocols MQTT would be preferable. 
* Cameras will be programmed to send a heartbeat message at regular intervals for as long as they are live.
* Cameras are pre-configured and ready to connect to the platform. The only requirement for the user installing the camera is to purchase a mobile data SIM card and plug it into the camera before turning it on.

# Use Cases

* Identify wildlife in an image and retain necessary information for future research.
* View device(camera) information
* Device self-registration
* Device-User association. If I buy a camera I want to be the one allowed to manage it, along-side the Wildelife.ai administrators
* Analyse Images
* Analyse video
* Observability - Monitoring and alerting for device status as well as whole system availability

# Risks

* Animal poachers or such criminals can take advantage of the information made available through this solution
* Cameras may not have the necessary hardware capabilities to connect to the message broker for heartbeat and updates so more manual interventions required

# Prioritised Architecture Characteristics ("illities")

## Extensibility
Wildlife.AI will encourage its community of users to purchase and install cameras in the wild, especially in places and regions where there might be endangered species or other rare wildlife. Therefore, Wildlife.AI could potentially deploy a large number of these cameras in the wild and, in the future, may allow other devices to be registered as long as they can provide the necessary information via the connectivity channels available. 

## Total Cost
Wildlife.ai are a non-profit organisation and thus any solution proposed must be cost-effective and not incur unnecessary expenses such as third party licenses or "idle" runtime costs. The proposed solution must allow for the use of Elastic cloud technologies. The implementation of this architecture must follow the cloud-native patterns.

## Scalability
The architecture must ensure that the system can accommodate an increasing number of cameras. People can buy and install cameras at their own expense, so the solution must be able to accommodate these cameras when they come online.
The application must also allow for a growing number of users, both regular users and camera administrators, to subscribe and operate on the platform.

## Security & Privacy
Access to the data captures regarding animals locations and other such details represent important pieces of information for the future of animals concerned. Therefore, a thorough vetting process must be applied for accepting users onto the platform. The user registration process must have 3 stages: 
1. Registration - users register and submit the required documentation
2. Vetting - Wildlife.ai ensures that the person wanting to use the platform has been properly verified.
3. Activation - After the user has been vetted and allowed onto the platform an activation email and unique URL are being generated so that the user can finalise the activation process.
The system must be secure so that the information regarding camera locations as well as Observations should only be accessible to screened users.
All data navigating through our solution is backed by latest TLS version and we recommend employing data repositories that can encrypt data at rest.

### Internal Certification Authority
We recommend implementing an **Internal Certification Authority** so that we can reduce the impact on comuptational resources on the Camera to implement a sophisticated OAuth 2.0 based token exchange or other authentication and authorisation mechanism to access the Event Broker. This can be implemented using products such as Hashicorp Vault, which offer the services for **Secrets Management** as well as **Internal CA**

## Fault-tolerance (Observability)
The platform must be highly observable, employing adequate monitoring and alerting facilities, so that it self-heals where possible but also that it informs the support teams to the error occurred.
The platform will also provide a way for monitoring and alerting in regards to the state of the cameras. The Observability service will subscribe to the Heartbeat topic and monitor the last time a camera was seen alive or battery low or any other metrics that it may identify or infer from the Heartbeat message, or lack of.

## Performance
The architecture must allow for the implementation of a performant system. The Performance of the system will be measured by the number of images processed in a time interval, by the number of events awaiting processing, by the response time for users' requests, the time a camera because available on the system once it's live, etc.

### Availability
We have identified availability as an important "illity" for our design but we considered that it doesn't have to apply to the whole system so a 1-nine level is more than sufficient for the following features:
* Endpoints for cameras to connect into as long as possible; Streaming platform.
* Web application for Widlife.ai users' access to images, cameras management and observations
Given the harsh environment wildlife.ai cameras operate in, the equipment must be able to endure and withstand physical damage as much as possible.

# Proposed Solution

We have taken the **Domain Driven Design** approach to understanding and braking down the problem to solve. We have identified a few contexts and components that should be implementing our solution, with the caveat that this separation is only the beginning and the business domains as well as observing the Conway’s Law, may result in different grouping of these components and different bounded contexts.

These **Bounded Contexts** will help in identifying the services that need to be implemented and reduce the unnecessary coupling between components, creating the acceptable size of features and functionality that need to be kept in a consistent grouping and relying on the same data store. 

Also, these contexts will help in identifying the Events that need to be generated by the different components in the system as well as the APIs to expose the information necessary for the contexts they interact with; it is also the best way to provide ***Privacy by Design***

The Bounded Contexts are enumerated below and detailed in the **[Bounded Contexts document](/docs/boundedcontexts/boundedcontexts.md)**
1. Camera Deployment and Management
2. Image Processing and Analysis
3. User Interaction and Management
4. Wildlife Monitoring and Identification
5. Streaming and Event Handling

Following on from the Bounded Contexts we are proposing the following architecture captured in [this diagram](/images/archdiagram/Components.jpg)

# Requirements

## REQ-001 - Users should be able to communicate with the camera remotely for reasons of management such as updating features, uploading subject images,uploading new ML models, downloading captured content, checking battery and other operational metrics <br />
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

## REQ

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

# Threat Model

# Architectural Decision Records

## Use of healthcheck pattern
## Use of API Gateway for exposing a specific API to access Observations and related material (videos, images)
## Pub/Sub message broker for receiving information from the cameras
## Event-driven microservices architecture
## Cameras must provide Software Over the Air functionality via specific topic in the message broker
