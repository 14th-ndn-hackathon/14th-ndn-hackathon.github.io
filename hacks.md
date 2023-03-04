---
layout: page
title: Hacks Proposals
---

{::options toc_levels="2,3" /}

* TOC
{:toc}

## 1.Pheonix: An attempt to use light-weight NDN on smartwatch


**Project Lead:**
- Saurab Dulal

<!-- Project Members: TBD -->
**Prefered Team Size:**
- 2-4

**Targeted participant**
- People with previous NDN experience

**How does your proposal benefit NDN?**
- Attempt to use NDN on smartwatches (more detail on the proposal)

**Briefly describe the tasks**
- Check if NDN-Lite could be used, fix any potential errors and revitalize it
- Attempt to compile and install NDN-Lite on the Android OS
- Test the installation with simple examples
- If the second task fails, look for other options

**Any specific tools or language**
- C++, Android

**Expected outcomes**
- Explore the possibilities of using NDN on Android
- Compile, install, and test ndn-lite on Android OS.



## 2. Bug Smash – Low Hanging Fruits


**Project Lead:**
- Junxiao Shi

<!-- Project Members: TBD -->
**Prefered Team Size:**
- 2-4

**Targeted participant**
- People with previous NDN experience

**How does your proposal benefit NDN?**
- improve platform software stability

**Briefly describe the tasks**

Several bugs in platform software that are easy to fix:

 - ndn-cxx may decode FreshnessPeriod as negative (#4997).
 - ndn-cxx misinterprets large dates in ValidityPeriod (#5176).
 - NFD faces/destroy should not destroy reserved faces (#4115).
 - ndncatchunks reports goodput=0 on ARMv7 (#5243).
 - NLSR hyperbolic routes have smaller cost than local apps (#5152).

Let's also get started on some new features:

 - ndn-cxx ValidatorConfig: multiple sig-type restrictions in checker (#5148).
 - NFD UDP multicast: toggle IPv4 and IPv6 independently (#4708).


**Any specific tools or language**
- C++, Boost C++ libraries

**Expected outcomes**
- Patches submitted to Gerrit for a subset of bugs, depending on actual team size and developer expertise.




## 3. NDN-DPDK support in python-ndn

**Project Lead:**
- Junxiao Shi

<!-- Project Members: TBD -->
**Prefered Team Size:**
- 2-4

**Targeted participant**
- People with previous NDN experience

**How does your proposal benefit NDN?**
- allow ndn-hydra to be actively used to solve problems which would popularize NDN

**Briefly describe the tasks**

NDN-DPDK management task:

 - In appv2 module, abstract out NFD management client related code.
 - Implement a management client for creating face and registering prefixes in NDN-DPDK forwarder.
 - Allow appv2.NDNApp to use either NFD or NDN-DPDK management client.

memif transport task:

 - Develop a Python C extension that wraps libmemif.
 - Develop a transport that calls into the C extension."


**Any specific tools or language**
- Python, C, GraphQL

**Expected outcomes**
- GitHub Pulls submitted for at least one task, depending on actual team size and developer expertise.



## 4. NDN 101
**Project Lead:**
- Varun Patil

<!-- Project Members: TBD -->
**Prefered Team Size:**
- 2-4

**Targeted participant**
- People new to NDN

**How does your proposal benefit NDN?**
- Learning about NDN outside a course is hard. You either need to read design documents or watch tutorials. With an interactive 101, newcomers will find it much easier to onboard to NDN concepts and development.

**Briefly describe the tasks**
 - Identify and gather the material to include
 - Present NDN in an interactive format.
 - Design and implement the 101 website.

Side task: revamp the named-data.net front page"


**Any specific tools or language**
 - HTML/CSS/TS in NDNts

**Expected outcomes**
 - And NDN 101 website
 



## 5. ndnSIM with go-ndn Application
**Project Lead:**
- Xinyu Ma

<!-- Project Members: TBD -->
**Prefered Team Size:**
- 4-5

**Targeted participant**
- People with previous NDN experience

**How does your proposal benefit NDN?**
- Currently, ndnSIM only supports ndn-cxx applications with some limitations. Enabling the usage of go-ndn applications in ndnSIM not only adds more applications to ndnSIM, but also provides a way to verify and test go-ndn code.

**Briefly describe the tasks**
 - Some patches (bridging code) on ndnSIM side and/or go-ndn side.
 - Evaluation on whether the proposed direction works or not.




**Any specific tools or language**
 - ndnSIM (C++), go-ndn (Go), WASM

**Expected outcomes**
 - Some patches (bridging code) on ndnSIM side and/or go-ndn side.
 - Evaluation on whether the proposed direction works or not.
