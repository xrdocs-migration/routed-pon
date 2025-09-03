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

Now let us explore the value Cisco Routed PON brings in and how it can be differentiated from the competitors

### Provider Connectivity Assurance (PCA)

The first differentiator is Cisco's Provider Connectivity Assurance. PCA is a solution designed to help broadband providers ensure the reliability, performance, and availability of their network infrastructure. It offers advanced visibility, proactive monitoring, and automated insights to identify and resolve potential connectivity issues before they impact services. This helps providers deliver a consistent and high-quality experience to their customers. The PCA solution comprises of three core components: sensors, an analytics engine, and a dashboard.

- Sensors are deployed at strategic locations within the network to monitor real-time connectivity for the data path.
- The analytics engine processes the collected data using advanced algorithms to proactively identify anomalies, detect performance bottlenecks, and generate actionable insights.
- The dashboard provides a centralized view of network performance, allowing administrators to monitor key metrics and troubleshoot issues.


![Screenshot 2025-09-02 at 2.34.15 PM.png]({{site.baseurl}}/images/Screenshot 2025-09-02 at 2.34.15 PM.png)

By deploying sensors at strategic points, providers are able to measure network and service performance with clear indication of health of the segments. Sensors are configured for data collection to monitor relevant metrics such as latency, delay, packet loss, throughput, and jitter. Thresholds (static or dynamic) are set to trigger alerts when performance deviates from acceptable levels. 

![Screenshot 2025-09-02 at 2.38.31 PM.png]({{site.baseurl}}/images/Screenshot 2025-09-02 at 2.38.31 PM.png)


The dashboard provides visual displays for delay metrics in real time to identify performance bottlenecks and diagnose common issues. 

![Screenshot 2025-09-02 at 3.29.05 PM.png]({{site.baseurl}}/images/Screenshot 2025-09-02 at 3.29.05 PM.png)

The analytics engine is used to identify trends and patterns in network performance, enabling proactive optimization. 

An assured network delivers significant business value across several key areas:

**Differentiated Services & Revenue Growth:** By enabling advanced capabilities like end-user customer portals, operators can offer premium, differentiated services, potentially capturing a 25-40% premium on standard offerings.

**Enhanced Customer Experience & Retention:** Proactive problem identification and resolution, facilitated by robust network assurance tools, ensure service level agreement (SLA) adherence, leading to superior customer satisfaction and improved retention.

**Optimized Capital Expenditure (CapEx):** Predictive analytics empower operators to strategically invest by identifying potential congestion points or latency issues, thus preventing unnecessary spending and optimizing network upgrades.

**Operational Expenditure (OpEx) Savings:** Early detection and resolution of network issues, often before customers are impacted, significantly reduce the Mean Time To Repair (MTTR) and minimize resource allocation for customer support and field operations.


### Network Service Orchestrator (NSO)

As discussed above, we can use either the web UI or netconf application to provision and monitor the PON network. We can use Cisco NSO for the same. [NSO] (https://www.cisco.com/site/us/en/products/networking/software/crosswork-network-services-orchestrator/index.html) is a multi-vendor, multi-domain service orchestration platform designed to automate the configuration and management of network services across diverse network devices and technologies. It acts as a central control point, abstracting away the complexities of individual device configurations and enabling end-to-end service delivery automation. NSO uses a model-driven approach (specifically YANG models) to define services and devices, allowing for consistent and reliable automation regardless of the vendor or technology involved.


**Business Case for Cisco NSO:**

Accelerated Service Delivery: Traditional manual configuration processes are slow and prone to errors. NSO automates these processes, significantly reducing the time it takes to design, provision, and activate new network services.

Cost Reduction (OpEx & CapEx): By automating tasks, NSO reduces the need for manual intervention, leading to lower operational expenditures. Its ability to optimize resource utilization and prevent errors can also indirectly impact capital expenditures by ensuring efficient use of existing infrastructure.

Improved Agility and Responsiveness: NSO enables rapid deployment of new services and modifications to existing ones, allowing organizations to be more agile and responsive to market changes.

Enhanced Service Assurance: NSO's transactional approach ensures that services are deployed correctly and consistently, improving overall network stability and service quality.

Bulk Configs: With pre-defined service templates providers can provision multiple services at a single time.

Model-Driven Automation (YANG): The use of YANG models provides a standardized, programmatic way to define network services and device configurations. This ensures consistency, reduces errors, and makes automation highly scalable and repeatable.

**Example service templates**

```
<config xmlns="http://tail-f.com/ns/config/1.0">
  <devices xmlns="http://tail-f.com/ns/ncs">
    <device>
      <name>rpon</name>
      <config>
        <pon xmlns="http://cisco.com/ns/yang/db">
          <onus>
            <onu>
              <name><mark>CIGG21b013a4</mark></name>
              <onu>
                <service-config>Unmodified</service-config>
              </onu>
            </onu>
          </onus>
        </pon>
      </config>
    </device>
  </devices>
</config>

```


In essence, Cisco NSO empowers organizations to transform their network operations from manual, error-prone processes to automated, agile, and reliable service delivery engines, crucial for modern digital infrastructures.n


- Secure DDoS 
  
   

## Conclusion
