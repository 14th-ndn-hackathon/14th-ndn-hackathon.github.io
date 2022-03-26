---
layout: page
title: Hacks Proposals
---

{::options toc_levels="2,3" /}

* TOC
{:toc}

## 0. Team formation

[Team member signup doc](https://docs.google.com/spreadsheets/d/1YlpFlj6EwxY1zssOoRCyzAoedKRQLXS-fsgs2S-Ce4M/edit?usp=sharing)

## 1. ~~NDN for In-Vehicle Networking~~

**Project Lead:**
- Christos Papadopoulos

**Description**
In-vehicle networks are rapidly evolving, moving away from existing in-vehicle network technologies such as controller area networking (CAN) and CAN-FD, LIN, Flexray, etc. to Automotive Ethernet. At the same time, in-vehicle several new communication architectures are being explored, such as data-centric and service-oriented architectures. In parallel, there are efforts such as the vehicle signal specification (VSS) by the W3C to standardize the naming of information (signals) in and out of vehicles. VSS is a hierarchical naming structure that is compatible with NDN naming.

In the near future, vehicles are expected to contain a mix of networking technologies, with automotive Ethernet used for high-speed communication (cameras, radar, LiDAR), and legacy networks for low bandwidth functions such as body control. Legacy networks have no security, authentication, provenance and are not resistant to DoS attacks.

In this project you will enhance NDN to support CAN communication. For this project it is sufficient to enable NDN clients to request CAN signals that are embedded in a CAN trace. These signals will be requested by the name assigned to them by the Vehicle Signal Specification [VSS project](https://github.com/COVESA/vehicle_signal_specification). You need not worry about the exact name of the signal in VSS as long as you use a VSS-like naming structure.

**Background**

The CAN bus is a network that broadcasts messages
to all participants, while supporting priorities based on the value of the CAN frame ID (lowest ID wins).
The payload of a CAN frame contains signals which are values that each
ECU reading a frame can decode. A frame can have various, arbitrary
formats. To help make sense of how signals map to which IDs 
vehicles use DBC files, which are text files that describe
these associations for each car model. Many opensource DBC files exist, 
which have been reversed engineered from real cars.
For a sample of how a CAN trace replay looks like while annotated through
info from a DBC, please check the comma.ai demo [here](https://cabana.comma.ai/)

The Linux kernel has support for CAN networks (socketcan)
as well as the ability to virtualize a CAN bus (vcan). Using builtin tools
like candump and canreplay we can examine in text form or issue messages on
either a real can network or our virtualized can bus.

**The Project**

In this project you will integrate CAN and NDN communication using a hierarchical naming tree that resembles VSS.

For the purposes of this project we will download a publicly available CAN
trace as well as the matching DBC file for that car and create an NDN
producer that publishes content containing the signals of each can frame
using descriptive names originating from the DBC file.

A possible path for this project would be:

- obtain a sample CAN log and a corresponding DBC file  
https://academictorrents.com/details/65a2fbc964078aff62076ff4e103f18b951c5ddb  
(chunks 1 and 2 are produced on a RAV4 while the rest are on a HONDA civic)  
https://github.com/commaai/comma2k19/  
https://github.com/commaai/opendbc
- bring up socketcan in vcan mode on your machine and use canreplay to replay the trace and candump to examine it.
- craft a program to read can frames either straight from the bus 
  https://github.com/linux-can/can-utils/blob/master/candump.c (lines 700-850)
  or by parsing the textual output of candump via a pipe.
- read a DBC file and create queues for each CAN ID declared in the dbc file
  that will accept signals belonging to each id.
- enqueue the messages as they are being read to their appropriate queue, 
  you could use FIFOs, sockets, or a message queue like zmq, the posix
  message queues available in linux (man 7 mq_overview) or your own construct.
- the final program could either connect to a socketcan interface or read a file and together with a DBC description provide the signal over an easy to consume NDN naming scheme.
- document your path and create a small blog-post/article that could be hosted as a resource of how to present a resource like an automotive dataset using NDN.

## 2. ~~Implementing gPTP in NDN~~

**Project Lead:**
- Christos Papadopoulos

**Description**
Time-Sensitive Networking (TSN) is a set of standards under development by the Time-Sensitive Networking task group of the IEEE 802.1 working group. gPTP is one protocol to implement TSN. This project will implement gPTP as an NDN forwarding strategy. IEEE 802.1AS-2011 defines the Generic Precision Time Protocol (gPTP) profile which employs UDP messages to establish a hierarchy of clocks and synchronize time in a gPTP domain formed by devices exchanging time events.

[TSN](https://en.wikipedia.org/wiki/Time-Sensitive_Networking)
|
[gPTP](https://docs.zephyrproject.org/latest/reference/networking/gptp.html)

**Background**

gPTP is a protocol that allows for participating
nodes to synchronize their clocks. It achieves that
by firstly knowing which node of the network has the most
accurate clock (called a Grandmaster) and by measuring
network delays. In its simplest form (no network delays) PTP
would involve a set of clocks on a network where a Grandmaster
is selected and all the other clocks would synchronize to the Grandmaster.
The protocol message to do that is called Sync, and would just contain the
current time (T1) of the Grandmaster.

When network delays are incorporated, each clock monitors the time 
when it received the Sync message from the Grandmaster (T1') and
calculates its offset. The clocks also need to measure round trip time
to their master. For that purpose the protocol uses the Delay_Req
and Delay_Resp messages. The clock sends a Delay_Req containing its
current time T2 to the Grandmaster, the Grandmaster marks the time that
it received it as T2' and responds back to the clock with a message containing T2'. Now the clock knows T1, T1', T2 and T2' and can calculate its offset as offset = 1/2 (T1' - T1 - T2' + T2).

Look at the protocol details at:
https://en.wikipedia.org/wiki/Precision_Time_Protocol.
Notice that the protocol also accounts for application to network stack delays
using extra messages (Follow_Up). In the case of PTP-capable hardware
these are not needed because the network card can timestamp a packet on
either receipt or transmission. For this initial implementation you
may ignore these and pretend that your timestamping is close to the real hardware timestamp.

**The Project**

For the purposes of this project the problem of selecting a 
grandmaster is out of scope. Also assume that you know which clock has 
the best accuracy (in an automotive application this would be the Gateway).
If no network delays were involved you could just 
design an NDN scheme that queries for /time/grandmaster and just receives the
current time from the grandmaster (Sync equivalent). 
That would allow you to determine T1 and T1'. Now to incorporate the RTT 
measurement you need to be able to determine the 
path that your interests towards the grandmaster follow. (It might be beneficial to look into prior work involving NDN-traceroute from
https://named-data.net/wp-content/uploads/2017/03/ndn-0055-2-trace.pdf)
Noted that some NFD forwarding strategies like ASF, 
calculate a sort of RTT for each face but this metric is not currently 
published somehow for applications to use
https://github.com/named-data/NFD/blob/master/daemon/fw/asf-strategy.cpp

The deliverables/workflow for this project could be:

- create the simple producer/consumer applications for Sync messages
- create a separate set of applications that, can calculate the RTT from an origin Clock to a Destination Clock (assume Origin and Destination have NDN names, for example they might be automotive ECUs)
- combine the applications above to build an initial PTP implementation
- (if time permits) implement the Delay set of messages to handle non PTP hardware
- (if time permits) consider the [security challenges](https://standards.ieee.org/wp-content/uploads/import/documents/other/d1-10_jesse_making_gptp_capable_for_secure_time_synchronization.pdf) in gPTP and consider how NDN could benefit it

Answer the following question: does NDN enable applications to build more/less/same efficient time synchronization compared to IP?

## 3. Integrate Content Connectivity and Location-Aware Forwarding (CCLF) into NFD

**Project Lead:**
- Muktadir Chowdhury

**Description**
Connectivity and Location-Aware Forwarding (CCLF) is a forwarding strategy for NDN-based MANETs.  CCLF broadcasts NDN packets and lets each node make independent decisions on whether to forward packets based on per-prefix performance measurements and any available geo-location information. In addition, it employs a density-aware suppression mechanism to reduce unnecessary packet transmissions. Moreover, we have developed a link adaptation layer for ad-hoc links to bridge the gap between CCLF and the capabilities of the underlying link.
CCLF is implemented and experimented with using ndnSIM. The goal of the project is to make CCLF functional in NFD and test it with minindn-wifi.
To accomplish the integration we have to:

- add the CCLF strategy and CCLF Measurement Accessor in the Strategy module;
- implement the Ad-Hoc Link Adaptation Layer which queues the outgoing packet and keeps track of the number of nodes around.

Participants' expected skills: C++, Python, familiarity with NFD and minindn-wifi.

[Paper](https://dl.acm.org/doi/pdf/10.1145/3405656.3418713)
|
[ndnSIM code](https://github.com/alvyC/CLF_ndnSIM/tree/vanet_fw_ndnsim)

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

## 6. Python-ndn Validator

**Project Lead:**
- Xinyu Ma

**Description**
Python-ndn is a client NDN library implemented in Python. Python-ndn has a validator that offers callback to applications with Data name and signature raw bytes. However, the validator implementation could be improved from two sides. First, the validator should recursively verify corresponding certificate signers till reaching the configured trust anchor. Second, an ideal validator should also execute trust schemas that enable data authenticity checkings. The two aspects are correlated, since the trust schema should provide a trust anchor for any specific packet validation scheme. 

One possible way to implement the trust schema in python-ndn is to take ndn-cxx’s trust schema language and implement its regex-based name matching in python. On the other hand, one can also implement a VerSec (nichols2021trust) parser and execute trust schemas by context-based rule matchings. Although the VerSec language has more expressive syntax in validation schemes, it lacks practices in other NDN libraries. 

Python-ndn already supports VerSec-based validators. In this project, we will provide the VerSec support on the data producer side to help facilitate the data signing, and investigate the possibility of providing VerSec support on ndn-cxx.

[python-ndn git repository](https://github.com/named-data/python-ndn)

## 7. Hydra Security Implementation

**Project Leads:**
- Justin Presley
- Proyash Podder

**Description**
Hydra, a distributed data repository system built over NDN, runs over a federation of storage servers provided by different user organizations. Users can publish files to Hydra, and the files can be shared following defined access policies. The Hydra codebase is constantly evolving and currently supports data insertion, deletion, and retrieval along with system queries. The security part however has not been formalized nor implemented yet. Therefore, in this project we would like to layout the foundations for Hydra security which include having a NOC (Network Operations Center) that authorizes Hydra nodes to join the system. The NOC also contains a trust schema of some sort that outlines who to trust in terms of users. This project is expansive (participants could authorize users based on their Google account). Nevertheless, we simply aim to at least get the foundation down so that we can confidently deploy and keep a Hydra instance running.

[Hydra git repository](https://github.com/justincpresley/ndn-hydra)
