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
{% include toc icon="table" title="Simplify, Monetize and Assure Your Broadband Networks" %}

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


### Why Move from Layer2 Access to [Routed Access]([[Reference](https://xrdocs.io/design/blogs/2023-11-15-routed-access-for-rural-broadband/)])?

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

## Cisco Routed PON Architecture

As described in the previous [blog](https://xrdocs.io/routed-pon/tutorials/cisco-routed-pon-whitepaper/), following are the main components. The first one is the physical hardware itself, that is the NCS540 or NCS5500 or NCS5700 router which is hosting the OLT pluggable as well as the PON controller software. The OLT pluggables can be plugged into the supported SFP+ ports. The second component is the OLT pluggable. It consists of the L1 transceiver as well as the L2 MAC features for PON functions. The third component is the ONUs/ONTs which will be used to plug the end devices. The fourth one is the PON manager which is a single web GUI for configuring, monitoring and diagnosing the end to end PON functionalities. The final one is the Cisco Provider connectivity assurance which will help to deliver assured services to the end users. Let us discuss how each components are stitched together. 

![Screenshot 2025-08-28 at 2.18.12 PM.png]({{site.baseurl}}/images/Screenshot 2025-08-28 at 2.18.12 PM.png)

Above is the system architecture, where all components are seamlessly integrated. The router hosts OLT pluggable modules, which connects to multiple ONUs/ONTs via a splitter. Communication between OLTs and ONUs is established using the standard OMCI protocol. The router runs PON controller software within a Docker container. The controller securely interacts with a database over IP-TLS; the database manages data storage and configuration information provided by the controller. The PON manager software offers both a graphical user interface and a REST API, accessing the database through a web server application. A Netconf server provides a standard Netconf interface and a customer-facing API for managing the PON network. The solution supports standard YANG models for configuring subscriber services within the PON network.

Currently solution is supported with the below Cisco products. 

| Cisco PIDs                      |
|---------------------------------|
| N540-24Z8Q2C-SYS/N540-ACC-SYS   |
| N540-24Q8L2DD-SYS               |
| N540X-16Z4G8Q2C                 |
| N540-28Z4C-SYS                  |
| N540-24Q2C2DD-SYS               |
| NCS-55A2-MOD-S                  |
| NCS-57C1-48Q6D                  |
| NCS-55A1-24Q6H-SS               |
| NCS-57C3-MOD                    |

**Note:** New PIDs are in roadmap

Cisco PON OLT is available in 2 variants

| PID                       | SFP-10G-OLT20-X                                   | SFP-10G-OLT20-I (available IOS-XR 25.4.1)         |
|---------------------------|---------------------------------------------------|---------------------------------------------------|
| Dimension(H x W x D)      | 8.55mm x 13.4mm x 80.65mm                         | 8.55mm x 13.4mm x 75.55mm                         |
| Data rate                 | Symmetric rates: 9.95G  upstream/9.95G downstream | Symmetric rates: 9.95G  upstream/9.95G downstream |
| Connector Type            | SC/UPC                                            | SC/UPC                                            |
| Distance                  | < 60 km                                           | < 20 km                                           |
| Operating temperature     | -20°C to 75°C                                     | -40°C to 85°C                                     |
| Typical Power Consumption | 2.475W                                            | 2.2W                                              |
| Cable Type                | Single Mode Fiber                                 | Single Mode Fiber                                 |
| ODN Class                 | N2                                                | PR30+                                             |

Below is the Cisco ONT/ONU portfolio

| PID                             | Port Details                                                                                              | Operating Temperature | Features and use cases                                                                                       |
|---------------------------------|-----------------------------------------------------------------------------------------------------------|-----------------------|--------------------------------------------------------------------------------------------------------------|
| ENC-10G-ONT-10 (IOSXR 25.4.1)   | 1x10G (RJ-45)                                                                                             | 0°C to 40°C           | -Small Desktop or wall mountable -Purpose built for small and medium size  business and Enterprise (SMB/SME) |
| ENC-10G-ONT-01PR (IOSXR 25.4.1) | 1 x 10M/100M/1G/2.5G (RJ-45) with POE                                                                     | -40°C to 65°C         | -Ruggedized, weather-proof and purpose  built for residential and small office  applications (SOHO)          |
| ENC-10G-ONT-14A (IOSXR 25.4.1)  | 4 x 100M/1GbE (RJ-45)  1 x 1/2.5/5/10G (RJ-45)  1 x FXS Voice Port (RJ-11)                                | 0°C to 40°C           | -Multi-port ONU with Analog Terminal  Adaptor purpose built for residential, MDU &  SMB/SOHO                 |
| SFP-10G-ONT20-I (IOSXR 26.1.1)  | 1x10G XGS PON SFP                                                                                         | -40°C to 85°C         | -Allows flexible deployments for low-cost  metro applications                                                |
| ENC-10G-ONT-14AS (CY 2026)      | 4 x 10M/100M/1G (RJ-45)  1 x 1G/2.5G/10G (RJ-45)  1 x FXS Voice port (RJ-11)  POE++ (90W) on 1G/10G ports | 0°C to 40°C           | -Power sourcing ONU with ATA ideal for  MDUs and buildings in hospitality industry for  PON LAN requirements |
| ENC-10G-ONT-14AW (CY 2026)      | 1 x 1G/2.5G/5G/10G (RJ-45)  4 x 10M/100M/1G (RJ-45)                                                       | 0°C to 40°C           | -Ideal for SMB/SME/SOHO applications                                                                         |
| ENC-10G-ONT-05GW (CY 2026)      | 4 x 10M/100M/1G (RJ-45)  1 x 1G/2.5G (RJ-45) WAN                                                          | 0°C to 40°C           | -WiFi 6 compliant gateway offering Gig+  speeds ideal for FTTx Deployments                                   |


## Competititive Analysis

Cisco's unique combination of a comprehensive feature set and a notably low cost within the Pluggable OLT category provides a significant competitive advantage. This positions Cisco favorably against other vendors, including those in both the pluggable and traditional chassis-based OLT segments, many of whom present higher cost structures. Cisco's major strengths includes:

- Universal [Access](https://www.cisco.com/site/us/en/products/networking/sdwan-routers/network-convergence-system-540-series/index.html) and [Aggregation](https://www.cisco.com/site/us/en/products/networking/sdwan-routers/network-convergence-system-5500-series/index.html)
- Advanced [routing](https://www.cisco.com/c/en/us/td/docs/iosxr/ncs5xx/routing/79x/b-routing-cg-79x-ncs540/implementing-static-routes.html) features
- Full support for next generation transport technologies ([SR/SRv6](https://www.cisco.com/c/en/us/td/docs/iosxr/ncs5xx/segment-routing/25xx/b-segment-routing-cg-25xx-ncs540.html))
- Support for [EVPN](https://www.cisco.com/c/en/us/td/docs/iosxr/ncs5xx/l2vpn/25xx/b-l2vpn-cg-25xx-ncs540.html) for overlay services 
- 3rd party ONT/ONU flexibility 
- MEF Certified products 
- [Secure DDoS Prevention](https://www.cisco.com/site/us/en/products/security/ddos-edge-protection/index.html) at the entry of the network
- Network Service Orchestration (NSO) for managing network via Netconf/YANG
- Enhanced Assurance using [Provider Connectivity Assurance](https://www.cisco.com/site/us/en/products/networking/software/provider-connectivity-assurance/index.html) (PCA) 
- Availability of Pay as you grow model
- Low Cost


## TCO savings 

## Cisco Value Add 
   - PCA
   - Secure DDoS 
   - NSO
   

## Conclusion 
