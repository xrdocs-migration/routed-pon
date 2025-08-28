---
published: true
date: '2025-08-28 11:00 -0700'
title: 'Simplify, Monetize and Assure Your Broadband Networks'
author: 'Tejas '
excerpt: 'This document deepdives into Cisco Routed PON solution '
tags:
  - iosxr
  - cisco
  - Routed PON
  - PON
  - Cisco Routed PON
  - Assurance
  - PCA
  - OLT
position: hidden
---
## Introduction

In our previous [blog post](https://xrdocs.io/routed-pon/tutorials/cisco-routed-pon-whitepaper/), we introduced the Cisco Routed PON solution, highlighting the challenges faced in current PON deployments and how Cisco’s approach addresses these issues. We also explored various government broadband initiatives and funding efforts designed to expand broadband access in underserved communities. Additionally, we provided an overview of the solution’s key components and high-level architecture.


In this whitepaper, we will take a deeper look into the Cisco Routed PON solution. We will examine its architecture in detail and explore how it enables broadband providers to differentiate their offerings and unlock new monetization opportunities

## Drivers for Broadband Network Transformation

Before we delve deeper into the solution, let’s examine current subscriber trends and consider their implications from an operator’s perspective.

![Screenshot 2025-08-28 at 11.15.57 AM.png]({{site.baseurl}}/images/Screenshot 2025-08-28 at 11.15.57 AM.png)

The shift towards the hybrid work model has increased the demand for additional bandwidth and necessitated enhancements to existing infrastructure to support next-generation applications and services. We are seeing a rise in emerging applications that enhance user experiences, such as augmented reality (AR), virtual reality (VR), and the metaverse. Gaming is a booming industry that requires low latency and high bandwidth, further driving broadband needs. It's not just residential users; but small and medium businesses are also seeing increased broadband demand to enhance their business models and provide new experiences for their end customers. These evolving subscriber demands, whether from home or business users, are challenging operators to innovate and upgrade their broadband networks.

How do these subscriber trends impact operators? In recent years, we have witnessed an unprecedented surge in data consumption—a trend that is only expected to accelerate with the growing adoption of AI technologies. Simply adding more bandwidth is not a sufficient solution. Instead, operators must select the right solutions and architectural upgrades to their networks in order to effectively meet the evolving and increasing demands of their customers.

## Moving away from Layer2 to Layer3

Cisco's Routed PON solution is designed to modernize rural broadband networks by moving from traditional Layer 2 (switching) access to a Layer 3 (routed) architecture. This approach places IP routing closer to subscribers, simplifying the network by reducing the number of protocols and layers needed between access and core, and enabling more scalable and manageable broadband deployments. 


### Why Move from Layer2 to [Routed Access]([[Reference](https://xrdocs.io/design/blogs/2023-11-15-routed-access-for-rural-broadband/)])?

**Scalability**: Layer 2 networks become complex and difficult to scale as the number of subscribers increases due to broadcast domains, MAC address learning, and spanning-tree limitations.

**Simplified Operations**: Routed access reduces the need for Layer 2 protocols and makes the network less prone to issues like loops and broadcast storms.

**Enhanced Security**: Segmentation and security are easier to implement at Layer 3, helping operators protect customer traffic.

**Improved Fault Isolation**: Routing protocols facilitate faster and more granular fault detection and isolation compared to Layer 2.

**Support for Advanced Services**: Layer 3 access enables better integration with modern IP services, automation, and policy enforcement, all of which are increasingly important as subscriber needs evolve.

In summary, transitioning from Layer 2 switching to Layer 3 routed access in rural broadband networks brings significant scalability, operational, and service innovation benefits, enabling operators to efficiently meet growing and evolving customer demands.


## Seamless integration of Routed PON with Cisco’s Agile Service Networking

Cisco [Agile Services Networking](https://www.cisco.com/c/en/us/products/collateral/service-provider/agile-services/agile-services-networking-so.html) is an architecture designed to power connectivity and customer experiences. It enables broadband service providers to monetize the delivery of assured services and networking. With Agile Services Networking, organizations can  deploy services closer to end-users for intelligent service delivery, remove complexity with simplified networks that converge network layers and services, and assure experiences with resilient networks and services enabled by AI-powered automation, observability, and security.

![agile.png]({{site.baseurl}}/images/agile.png)

Routed PON is a validated use case within Cisco Agile Service Networking, illustrating how PON can be seamlessly integrated into a converged, agile infrastructure to deliver scalable and flexible broadband services. By reducing the OLT to a pluggable module, it can be easily incorporated into access and aggregation routers. This integration simplifies the network with a single operating system, enabling operators to benefit from unified management and advanced service capabilities.
By leveraging advanced transport technologies such as Segment Routing (including SRv6) and overlay solutions like EVPN, broadband providers can build programmable networks that are ready to meet future demands. Cisco's [cloud native Broadband Network Gateway(BNG)](https://www.cisco.com/c/en/us/td/docs/routers/asr9000/software/25xx/cloud-native-bng/configuration/guide/b-cnbng-user-plane-cg-asr9000-25xx/cloud-native-bng-overview.pdf) acts as a central access point for subscriber connectivity. The BNG manages user authentication, traffic routing, and quality of service (QoS), ensuring reliable broadband access for large groups of users at the scale required by the providers. This centralized control provides operational efficiency, scalability for managing large subscriber bases, and enables the delivery of diverse broadband services such as internet, IPTV, and VoIP through a unified connection.
Furthermore, Cisco's solution leverages advanced hardware technologies, including [TAM chips] (https://www.cisco.com/c/en/us/td/docs/iosxr/ncs5500/security/25xx/configuration/guide/b-system-
security-cg-ncs5500-25xx.html), to enhance network security.

## Architecture
