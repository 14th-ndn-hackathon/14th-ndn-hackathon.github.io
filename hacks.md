---
layout: page
title: Hacks Proposals
---

{::options toc_levels="2,3" /}

* TOC
{:toc}

## 1. NDN for In-Vehicle Networking
**Project Lead:**
- Christos Papadopoulos

**Description**
In-vehicle networks are rapidly evolving, moving away from existing in-vehicle network technologies such as controller area networking (CAN) and CAN-FD, LIN, Flexray, etc. to Automotive Ethernet. At the same time, in-vehicle several new communication architectures are being explored, such as data-centric and service-oriented architectures. In parallel, there are efforts such as the vehicle signal specification (VSS) by the W3C to standardize the naming of information (signals) in and out of vehicles. VSS is a hierarchical naming structure that is compatible with NDN naming.

In the near future, vehicles are expected to contain a mix of networking technologies, with automotive Ethernet used for high-speed communication (cameras, radar, LiDAR), and legacy networks for low bandwidth functions such as body control. Legacy networks have no security, authentication, provenance and are not resistant to DoS attacks.

In this project we will create an in-vehicle testbed by porting NDN into an emulated in-vehicle network. We will use Raspberry Pis to emulate in-vehicle communication and VSS to name signals. Raspberry Pis equipped with CAN hats can implement three different networking technologies: CAN, LIN and Ethernet. We will use all three. Communication will be driven by the ROAD CAN trace collected by ORNL. We will test various aspects, such as security, integrity, authentication, resistance to DoS attacks, transport efficiency including error recovery and latency. We will create translators between CAN frames and NDN named objects. We will explore the design, implementation, and performance of communication over the testbed.

There are several outcomes from this project:
- The namespace design
- The impact of shifting to a data-centric implementation such as NDN
- The impact on performance in terms of throughput and latency
- An evaluation of security-related properties
- A qualitative evaluation of interoperability

## 2. Implementing gPTP in NDN
**Project Lead:**
- Christos Papadopoulos

**Description**
Time-Sensitive Networking (TSN) is a set of standards under development by the Time-Sensitive Networking task group of the IEEE 802.1 working group. gPTP is one protocol to implement TSN. This project will implement gPTP as an NDN forwarding strategy. IEEE 802.1AS-2011 defines the Generic Precision Time Protocol (gPTP) profile which employs UDP messages to establish a hierarchy of clocks and synchronize time in a gPTP domain formed by devices exchanging time events.

[TSN](https://en.wikipedia.org/wiki/Time-Sensitive_Networking)
[gPTP](https://docs.zephyrproject.org/latest/reference/networking/gptp.html)

## 3. Integrate Content Connectivity and Location-Aware Forwarding (CCLF) into NFD
**Project Lead:**
- Muktadir Chowdhury

**Description**
Connectivity and Location-Aware Forwarding (CCLF) is a forwarding strategy for NDN-based MANETs.  CCLF broadcasts NDN packetsand lets each node make independent decisions on whether to forward packets based on per-prefix performance measurements andany available geo-location information. In addition, it employs a density-aware suppression mechanism to reduce unnecessary packet transmissions. Moreover, we have developed a link adaptation layer for ad-hoc links to bridge the gap between CCLF and the capabilities of the underlying link.
CCLF is implemented and experimented with using ndnSIM. The goal of the project is to make CCLF functional in NFD and test it with minindn-wifi. 
To accomplish the integration we have to 
- add the CCLF strategy and CCLF Measurement Accessor in the Strategy module
- implement the Ad-Hoc Link Adaptation Layer which queues the outgoing packet and keeps track of the number of nodes around.

## 4. NDNSD: Service Publishing and Discovery in NDN
**Project Lead:**
- Saurab Dulal

**Description**
NDNSD is a fully distributed and general-purpose service discovery protocol for NDN that works in a wide range of environments, e.g., LAN, WAN, and IoT. It provides an API for applications to advertise and discover services. Internally, it uses NDN Sync for service announcement and discovery. In addition, it offers several design features such as hierarchical naming, service information specification, measurement information, and service accessibility. Among these 
features, we have fully implemented service publishing and discovery API and naming, and have partially implemented service information specification (a.k.a service-info). The goal of this project is to implement 1) the service-information specification (complete the implementation) ii) service accessibility, and iii) measurement information. If time permits, we will also evaluate NDNSD against some of the existing protocols (e.g. SPDP).

[Current implementation](https://github.com/dulalsaurab/NDNSD)
[NDNSD](https://umwa.memphis.edu/etd/index.php/view/download/sdulal/6651/6651.pdf)

## 5. Profiling YaNFD
**Project Lead:**
- UCLA team

**Description**
[YaNFD](https://github.com/named-data/YaNFD) is an NDN forwarder implemented in Golang. Since Go can use concurrency very efficiently, it is expected that YaNFD should have superior performance compared to NFD, which is single threaded. However, the performance gains observed currently are not as good as expected. This project involves profiling and investigating why the performance of YaNFD is not as expected.
