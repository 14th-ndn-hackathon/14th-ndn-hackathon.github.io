---
layout: page
title: Hacks Proposals
---

{::options toc_levels="2,3" /}

* TOC
{:toc}

## <del>1. Passive Name Visualizer</del>

#### **[Pitch Slides]({% asset ndn-hackathon2105-proposal1.pdf @path %})**

**Project Lead:**
- Junxiao Shi

**Preferred Team Size:**
- 2

**Target Participants:**
- People new to NDN development

**How will your proposal benefit NDN?**
- Insights into network behavior

**Briefly describe the tasks:**
Build upon the namevis project from ndnhack10, add two new features:
- server-side name filtering and aggregation
- time range selection (from pcap file)

**Any specific tools or languages?**
- Go
- Chart.js

**Expected Outcomes:**
- New features implemented

## <del>2. NDN Experiments on Fed4FIRE</del>

#### **[Pitch Slides]({% asset ndn-hackathon2105-proposal2.pdf @path %})**

**Project Lead:**
- Junxiao Shi

**Preferred Team Size:**
- 3

**Target Participants:**
- People new to NDN development

**How will your proposal benefit NDN?**
- Quick start for NDN experimentation on a testbed

**Briefly describe the tasks:**
Build upon existing app at https://rspec.ndn.today, add new features:
- Import topology from Mini-NDN topology file.
- Support NFD and NLSR.
- Add telemetry collection for "Docker registry over NDN" proxy program.

**Any specific tools or languages?**
- Docker
- PHP
- Go

**Expected Outcomes:**
- At least two new features implemented

## 3. NDN-FCH: The Big Rewrite

#### **[Final Slides]({% asset final-3-ndn-fch.pdf @path %})**
#### **[Pitch Slides]({% asset ndn-hackathon2105-proposal3.pdf @path %})**

**Project Lead:**
- Junxiao Shi

**Project Members:**
- Eric Newberry
- Junxiao Shi
- Muhammad Nuzaihan
- Zhiyi Zhang

**Preferred Team Size:**
- 4

**Target Participants:**
- People with NDN code development experience

**How will your proposal benefit NDN?**
- More robust service

**Briefly describe the tasks:**
Improve NDN-FCH service:

- Allow more transport protocols, including IPv4 & IPv6, UDP, WebSockets, HTTP/3 over QUIC
- Perform periodical reachability tests from around the world
- Deploy a frontend on Cloudflare Workers, avoid single point of failure
- Download GeoLite2 database with MaxMind license key
- Collect RTT feedback from clients

**Any specific tools or language**
- Go
- Python
- JavaScript

**Expected outcomes**
- Complete features 1-4

## <del>4. Bug Smash: Low Hanging Fruits</del>

#### **[Pitch Slides]({% asset ndn-hackathon2105-proposal4.pdf @path %})**

**Project Lead:**
- Junxiao Shi

**Preferred Team Size:**
- 3

**Target Participants:**
- People with NDN code development experience

**How will your proposal benefit NDN?**
- Fix bugs in platform software

**Briefly describe the tasks:**
- NFD faces/destroy should not destroy reserved faces (#4115).
- NFD crashes upon binding to a tentative IPv6 address (#5155).
- NFD crashes upon receiving TCP RST (#5158).
- PSync relies on Name URI syntax that is non-portable (#4838).
- NLSR crashes if security is disabled (Slack#nlsr 2021-03-30).

**Any specific tools or language**
- C++
- Boost C++ libraries
- Gerrit

**Expected outcomes**
- Bugfixes submitted to Gerrit, project members are expected to follow-up until they are merged

## <del>5. MetaSync Protocol</del>

#### **[Pitch Slides]({% asset ndn-hackathon2105-proposal5.pdf @path %})**

**Project Lead:**
- Justin C Presley

**Preferred Team Size:**
- 3

**Target Participants:**
- People new to NDN development

**How will your proposal benefit NDN?**
- Expands on svs to allow more data producers and nullifying datasets

**Briefly describe the tasks:**
- Implement said design, maybe include more improvements within the design

**Any specific tools or language**
- Python starting
- C++ if we can

**Expected outcomes**
- Have an implemented improved sync protocol

## 6. NDN Compute Simulator (ndnCSim)

#### **[Final Slides]({% asset final-6-ndncsim.pdf @path %})**
#### **[Pitch Slides]({% asset ndn-hackathon2105-proposal6.pdf @path %})**

**Project Lead:**
- Muhammad Atif Ur Rehman

**Project Members:**
- Muhammad Atif Ur Rehman
- Muhammad Imran
- Muhammad Salahuddin
- Sana Fayyaz

**Preferred Team Size:**
- 4

**Target Participants:**
- People with NDN code development experience

**How will your proposal benefit NDN?**
- In-network computation and specifically edge cloud computing has attracted extensive attention in the recent past from both academia and Industry. The common goal of these technologies is to enable the networking nodes to perform computations. Such networking nodes include 1) edge computing node, 2) the resource-full routers between an edge node and cloud node and 3) the cloud node itself. Various NDN-based in-network computation solutions have been proposed by the researchers, indicating the widespread interest of the NDN research community in edge cloud computing and in-network computations. However, unfortunately, the default implementation of the ndnSIM simulator does not provide the basic realization of in-network computations, leaving the NDN researchers with the only option of implementing the computation mechanism from scratch. To save the researchers time and to provide them the basic implementation of in-network computation, this hackathon project aims to add the computation functionality in ndnSIM. As a result, the NDN research community will be greatly benefited from the above-mentioned implementation, as by utilizing ndnCSIM the researcher can leverage the basic implementation of in-network computations in vanilla-ndnSIM.

**Briefly describe the tasks:**
This hackathon project aims to complete the following task.
- Enable the consumer node to set the computation-based naming scheme.
- Enable the intermediate nodes to perform computations based on the received compute request in the Interest packet. To mimic the computation behavior, we will add different computation models. Moreover, we will also add the functionality to monitor the resource consumption of the intermediate nodes. For example, by default, the intermediate node resource utilization will be 0%, however, as soon the computation requests arrive, the resource utilization will be increased to let say 10% depending on nature (type) of the task. Thus, if 100% resource utilization is met, the intermediate node offloads the request to the next node. All of the above-mentioned implementations will be incorporated into the NFD codebase.
- Develop NDN compute-based producer application in an apps folder. Similar to the intermediate node, the producer node application also monitors resource utilization. However, different from the intermediate node, the producer node computes the application adds the compute request in the waiting pool if the resources are fully occupied, and performs the computation after the resource availability.

**Any specific tools or language**
- C++
- vanilla-ndnSIM

**Expected outcomes**
- The implementation for in-network computations in ndnSIM simulator.

## 7. NDN Play

#### **[Final Slides]({% asset final-7-ndn-play.pdf @path %})**
#### **[Pitch Slides]({% asset ndn-hackathon2105-proposal7.pdf @path %})**

**Project Lead:**
- Varun Patil

**Project Members:**
- Tianyuan Yu
- Varun Patil

**Preferred Team Size:**
- 1

**Target Participants:**
- People with NDN code development experience

**How will your proposal benefit NDN?**
- A web interface to create and play with NDN topologies, similar to miniNDN, but running fully in the browser without any backend. This will be useful for beginners to understand NDN.

**Briefly describe the tasks:**
- Create the web interface
- Simulate a rudimentary JavaScript NDN forwarder or port an existing one to JS

**Any specific tools or language**
- JavaScript
- NDNts

**Expected outcomes**
- Full web interface that can be used by NDN beginners to simulate networks.

## 8. Mini-NDN Improvements

#### **[Final Slides]({% asset final-8-mini-ndn.pdf @path %})**
#### **[Pitch Slides]({% asset ndn-hackathon2105-proposal8.pdf @path %})**

**Project Leads:**
- Saurab Dulal
- Alexander Lane

**Project Members:**
- Adam Thieme
- Ashiq Rahman
- Justin Presley
- Saurab Dulal

**Preferred Team Size:**
- 3

**Target Participants:**
- People new to NDN development

**How will your proposal benefit NDN?**
- Mini-NDN: an easy to install and use NDN emulator environment

**Briefly describe the tasks:**
- Helper for ndn-trac-generator and a basic consumer producer
- Mini-NDN GUI topology editor and documentations
- Improve Mini-NDN installation script and Vagrantle, install ndn packages from PPA and investigate python compatibility issues
- Improvements in user guide with a very simple topology and adding demo video

**Any specific tools or language**
- Mini-NDN
- Python
- Shell
- Vagrant
- C++

**Expected outcomes**
- Improved Mini-NDN, easy to install and play

## 9. CertCoalesce: NDN Certificate Pools

#### **[Final Slides]({% asset final-9-cert-coalesce.pdf @path %})**
#### **[Pitch Slides]({% asset ndn-hackathon2105-proposal9.pdf @path %})**

**Project Leads:**
- Alexander Afanasyev
- Proyash Podder

**Project Members:**
- Alexander Afanasyev
- Proyash Podder
- Xinyu Ma

**Preferred Team Size:**
- 3

**Target Participants:**
- People new to NDN development

**How will your proposal benefit NDN?**
- Efficiently manage virtually unlimited pools of public/private keys and certificates to save storage on constrained devices.

**Briefly describe the tasks:**
- Based on initial skeleton, sync up to the proposed design
- Create a python package
- Create a simple demo and write (interactive) documentation

**Any specific tools or language**
- Python
- Basic math skills

**Expected outcomes**
- A working Python package, simple demo, and initial skeleton of documentation
