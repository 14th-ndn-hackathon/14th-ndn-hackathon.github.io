---
layout: page
title: Hacks Proposals
---

{::options toc_levels="2,3" /}

* TOC
{:toc}

## 1. Implementing Mnemosyne, An Immutable Logger

#### **[Pitch Slides]({% asset ndn-hackathon2110-proposal1.pdf @path %})**

**Project Lead:**
- Siqi Liu

**Preferred Team Size:**
- 4

**Target Participants:**
- People with NDN code development experience

**How will your proposal benefit NDN?**
- Mnemosyne provides a logging solution for NDN based distributed applications.

**Briefly describe the tasks:**
- Implementing a prototype for Mnemosyne base on the design in the ICN poster.

**Any specific tools or languages?**
- NDN-CXX, SVS, LevelDB

**Expected Outcomes:**
- The prototype codebase are expected to be ready for demo and evaluation. It should be ready to be tested on Hydra, the NDN distributed Repo.

## 2. YaNFD UI

#### **[Pitch Slides]({% asset ndn-hackathon2110-proposal2.pdf @path %})**

**Project Lead:**
- Xinyu Ma

**Preferred Team Size:**
- 2

**Target Participants:**
- People new to NDN development

**How will your proposal benefit NDN?**
- A UI can make YaNFD easier to use, especially to new developers who are using Windows or not familiar with command-line tools. Hopefully, a user-friendly UI can attract more people to try out NDN.

**Briefly describe the tasks:**
- Write a command-line UI for YaNFD that can manage faces and routes.

**Any specific tools or languages?**
- Go

**Expected Outcomes:**
- A new executable yanfdui which runs as YaNFD with the newly developed UI, where users can view/add/delete faces and routes through UI directly.

## 3. ~~Passive Name Visualizer~~

#### **[Pitch Slides]({% asset ndn-hackathon2110-proposal3.pdf @path %})**

**Project Lead:**
- Junxiao Shi

**Preferred Team Size:**
- 2

**Target Participants:**
- People new to NDN development

**How will your proposal benefit NDN?**
- insights into network behavior

**Briefly describe the tasks:**
"Build upon 10th NDN hackathon project:
- upgrade to Chart.js version 3
- server-side name filtering and aggregation
- time range selection (from pcap file)"

**Any specific tools or language**
- Go, NDNgo, JavaScript, RE:DOM, Chart.js

**Expected outcomes**
- demo of the improved system

## 4. ~~NDN-FCH Feedback Loop~~

#### **[Pitch Slides]({% asset ndn-hackathon2110-proposal4.pdf @path %})**

**Project Lead:**
- Junxiao Shi

**Preferred Team Size:**
- 2

**Target Participants:**
- People new to NDN development

**How will your proposal benefit NDN?**
- better connectivity from end hosts

**Briefly describe the tasks:**
Build upon 11th NDN hackathon project:
* Design a protocol that allows end hosts to submit reachability & RTT feedback to the beacon server.
* Develop the beacon server that saves feedback to database.
* Develop client app that submits the feedback.

Note: influencing NDN-FCH response with feedback data would be future work.

**Any specific tools or language**
- beacon server: Go, MySQL; client app: Go or TypeScript or C++

**Expected outcomes**
- Present protocol design; demo feedback generation and collection; present ideas of how to improve NDN-FCH response with feedback

## 5. ~~Bug Smash – Low Hanging Fruits~~

#### **[Pitch Slides]({% asset ndn-hackathon2110-proposal5.pdf @path %})**

**Project Lead:**
- Junxiao Shi

**Preferred Team Size:**
- 4

**Target Participants:**
- People with NDN code development experience

**How will your proposal benefit NDN?**
- improve platform software stability

**Briefly describe the tasks:**
Fix the following bugs in platform software:
- ndn-cxx misinterprets large dates in ValidityPeriod (#5176).
- NFD faces/destroy should not destroy reserved faces (#4115).
- NFD crashes upon receiving TCP RST (#5158).
- PSync relies on Name URI syntax that is non-portable (#4838).
- NLSR crashes if security is disabled (Slack#nlsr 2021-03-30).
- NLSR hyperbolic routes have smaller cost than local apps (#5152).
- ppa-packaging unnecessarily uses sudo.
- ppa-packaging uses obsolete ndnsec-* wrappers.
- ppa-packaging unnecessarily depends on Python2 and libboost-all-dev.

**Any specific tools or language**
- C++, Boost C++ libraries, Debian packaging

**Expected outcomes**
- Patches submitted to Gerrit for a subset of bugs, depending on actual team size and developer expertise.

## 6. ~~PIT Token in ndn-cxx and python-ndn~~

#### **[Pitch Slides]({% asset ndn-hackathon2110-proposal6.pdf @path %})**

**Project Lead:**
- Junxiao Shi

**Preferred Team Size:**
- 2

**Target Participants:**
- People with NDN code development experience

**How will your proposal benefit NDN?**
- unlock better performance

**Briefly describe the tasks:**
Accept and return PIT token on producer side of ndn-cxx and python-ndn.
Test with YaNFD (via TCP transport with non-local scope).

**Any specific tools or language**
- C++, ndn-cxx, Python 3, python-ndn

**Expected outcomes**
- Get it implemented in at least one library, depending on developer expertise

## 7. Mini-NDN improvements

#### **[Pitch Slides]({% asset ndn-hackathon2110-proposal7.pdf @path %})**

**Project Lead:**
- Saurab Dulal

**Preferred Team Size:**
- 3

**Target Participants:**
- People new to NDN development

**How will your proposal benefit NDN?**
- Mini-NDN can be used by staters to play with NDN, where as intermediate/experts on NDN can use it to perform real emulated experiments.

**Briefly describe the tasks:**
- Helper for ndn-traffic-generator and a basic consumer producer
- Mini-NDN GUI topology editor and documentations
- Improve Mini-NDN installation script and Vagrantfile, install ndnpackages from PPA and investigate python compatibility issues
- Improvements in user guide with a very simple topology and addingdemo video

**Any specific tools or language**
- Mini-NDN, Python, Shell, Vagrant, C+

**Expected outcomes**
- Improved Mini-NDN, easy to install and play
