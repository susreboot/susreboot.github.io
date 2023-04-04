---
title: "AZ-900 Cert. - Module 1"
date: "2023-03-20"
categories: 
  - "azure"
  - "cloud"
  - "learning"
  - "tutorial"
  - "windows"
---

Source: [https://marczak.io/az-900/](https://marczak.io/az-900/)

https://youtu.be/Pt9LelJ0fL0?list=PLGjZwEtPN7j-Q59JYso3L4\_yoCjj2syrM

* * *

**Module 1 - Describe cloud concepts (15-20%)**

- Skills Learned
    - Describe what is [**Cloud Computing**](onenote:#Learning%20Modules&section-id={1801AE52-E18F-4580-8E6C-7B80BF769E62}&page-id={5FC2E363-6494-4B0E-9AD8-881F0E1BA407}&object-id={739D5A59-7E31-4D5A-9614-55AE4FC3A772}&CE&base-path=https://d.docs.live.net/35b5d1d6c43c62b1/Documents/AZ-900%20Studying/Quick%20Notes.one)
    
    - Describe terms such as **High Availability**, **Scalability**, **Elasticity**, **Agility**, **Fault Tolerance**, and **Disaster Recovery**

- Episode Resources
    - [📚 Study cheat sheet](https://marczak.io/az-900/episode-01/cheat-sheet)
    
    - [🧠 Practice Test](https://marczak.io/az-900/episode-01/practice-test)

- Study Guide
    -  [Microsoft Learn: Explore key cloud concepts](https://docs.microsoft.com/learn/modules/discuss-why-cloud-services/4-explore-key-cloud-concepts?WT.mc_id=AZ-MVP-5003556)
    
    -  [Azure Homepage: Cloud computing terms](https://azure.microsoft.com/overview/cloud-computing-dictionary/?WT.mc_id=AZ-MVP-5003556)
    
    - [🌐 Wikipedia: Cloud Computing Characteristics](https://en.wikipedia.org/wiki/Cloud_computing#Characteristics)

* * *

**Contents**

Cloud Computing  
High Availability (HA)  
Scalability  
Elasticity  
Agility  
Fault Tolerance (FT)  
Disaster  
Disaster Recovery (DR)

* * *

**Cloud Computing**

- Cloud computing is a  delivery model for services like the following. There are many other services but these are the 4 covered on the AZ-900 Exam. All these services are delivered over the internet.

- Storage
    - Files – Store of business data in the could (aka files)
    
    - Databases – Azure offer fully managed relational, NoSQL, and in-memory databases. These databases can span from proprietary and open-source engines and are determined by the needs of a developer.

- Compute Power
    - Virtual Machines (Linux/Windows/Containers)

- Networking
    - Secure networking between cloud components
    
    - Networking with business network

- Analytics
    - Performance Data – Periodically collected numeric data relating to the performance of a device or a component of the device.
    
    - Telemetry - The measurement of data (electrical or physical) and remote transmission of this data.

**Scalability**

- Scalability is the ability to "scale". Scaling is the process of;
    - Allocating (adding) resources
    
    - Deallocating (removing) resources

- Vertical Scaling – Increasing resources (CPU/RAM/GPU/STORAGE/NETWORK BANDWIDTH) up or down to meet the needs of the virtual service function (hence the name "vertical" ↑↓ )
    - Scaling up (↑) – Increasing resources to meet the virtual services need.
    
    - Scaling down (↓)– Decreasing resources to match the needs of the virtual service.

![](images/image-1.jpeg)

- Horizontal Scaling (↔) – Adding similar machines to equally distribute the service workload across machines. This can be increased or decreased on a need basis and can also occur automatically.
    - Scaling out (→) - Increasing the amount of resources/instances needed for virtual services.
    
    - Scaling in (←) - Decreasing the amount of resources/instances needed for virtual services.

![](images/image.jpeg)

**Elasticity** 

- Elasticity is the ability to scale dynamically to match resources sufficient for the given virtual service/workload. If **scaling** is happening quickly, it is referred to as **Elasticity.**

**Agility**

-  There are two ways to allocate resources in the cloud; manually or automatically (using scripting).  Regardless of the chosen method of allocation/deallocation, with agility the ability to allocate and deallocate resources to scale can be done quickly based on the environment or business needs.

**Fault Tolerance**

- Fault tolerance is the ability to remain up and running during component and service failures. Maintaining no single point of failure within the datacenter, preventing the chance of a virtual service failure.
    - Fail-overs - A plan to shift traffic to a redundant system in case the primary system fails.
        - A common example of a fail-over with a database would be; having two systems, with the second system containing a copy of the database. All ongoing changes would be synced to this second database system and would not be in-use until a fail-over is triggered and the secondary machine would take over the job of the primary machine (becoming the primary machine).
        
        - **Azure Traffic Manager** (a DNS-based traffic balancer) can be used to fail-over from a failing primary system to a stand-by secondary system.

![](images/image.png)

**Disaster**

- A disaster is a serious disruption of services caused by natural or human-induced causes/errors.

**Disaster Recovery (DR)**

- Disaster Recovery is the ability to recover from an event that has taken down a virtual service or region (a disaster).
    - A basic Disaster Recover for Azure would be to create two instances of a virtual service in separate regions (aka separate datacenters) and setting up replication between the two regions.
        - In front of these two replicated instances, DNS routing should be configured for the user to be automatically transferred to the secondary DR site in the event of disaster. 

**High Availability (HA)**

- High Availability (HA) is the ability to jeep services running for extended periods of time with very little downtime.
    - Availability can be calculated by Year, Month, or day and uses the formula:
        - MTBF (uptime) - **M**ean **T**ime **B**etween **F**ailure
        
        - MTTR (downtime) - **M**ean **T**ime **T**o **R**epair
            - **Availability =** Uptime(MTBF)/ uptime(MTBF) + downtime(MTTR) \* 100% = **X%**
