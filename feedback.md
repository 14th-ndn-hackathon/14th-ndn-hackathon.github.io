## 9th NDN Hackathon Feedback & Future Work
---
### [Project 2]: NFD on OpenWrt Home Router
**Feedback:**

- Not mentioned.

**Future work:**

1. Create config page for ndn-autoconfig section.
2. Add dynamic updates for face status page.
3. Integrate ndn6-file-server in UCl and LuCl.
4. Integrate ndncert client in LuCl
5. Publish as opkg package(s).
---

### [Project 5]: Simulating Multicast Supression Scheme 
**Feedback:**

- Not mentioned.

**Future work:**

- Not mentioned.
---

### [Project 7]: Service Discovery for IoT Devices through PSync FullSync
**Feedback:**

(Problems with current PSync implementation for IoT)
1. It doesn't efficiently support an application to be a full consumer only - one who doesn't 
produce any data.
2. Harder to deploy PSync in low constraints IoT devices (consumers only) because of its intensive
IBF related computation (compression, hashing, insertion ...) - mostly not needed if no data is
produced,

**Future work:**
1. Complete the porting of full consumer in ndn-lite and release the code
2. Integrate in esp8266ndn library as it support ndn-lite
3. Develop a sync protocol adaptor to support various sync protocol (similar to what NLSR is doing
right now)
---

### [Project 8]: NDN Mailing List Search Tool
**Feedback:**
- Not mentioned

**Future work:**
- Right now, the project only support searching in ndn-interest mailing list, in the future, the
project plans to support more NDN mailing lists.
---

### [Project 9]: NFD-Android Enhancements
**Feedback:**
- Lack of API to retrive strategy choice for a given prefix

**Future work:**
- Uploading the NFD-Android ping server patch.
---

### [Project 10]: Enhanced Testbed Monitoring and FCH Service
**Feedback:**
1. Send control command to `/localhop/nfd/rib/register`
2. "Origin" field of control parameters MUST contain a magic number (65) for client-to-nlsr
readvertisement to work
	- Not documented anywhere!
3. Even with the origin value, the control command was still being rejected by the remote NFD
	- Impossible to debug
	- RIB management protocol does not document potential error codes, or anything else regarding
the format of error messages
	- PyNDN does not provide a reason in the prefix registration failure callback
	- NFD knows the root cause (in this case a slightly out-of-sync clock) but only encodes a generic
"command rejected" in the response packet
4. Debugging
	- SSH access to testbed router (LIP6)
	- Enable debug loggign (which module? Hint: not what you'd think)
	- Command interest validator is in ndn-cxx (how to discover logger module name?)
	- Need to group logging by logical function performed, not by C++ class that implements it
	- "Timestamp is outside the grace period for key /foo/bar/..."

**Future work:**
- Not mentioned.
---

### [Project 11]: NDN-Lite over LoRa Network
**Feedback:**
- Not mentioned

**Future work:**
- Not mentioned.
---

### [Project 12]: Migrate multipath forwarding strategy to latest ndnSIM and integrate ns3 TrafficControlLayer
**Feedback:**
- Not mentioned.

**Future work:**
- Not mentioned
---
### [Project 13]: NDNCERT-v2: Debug, Deploy, Dominate
**Feedback:**

Crashed
- Ndncert-client
	- Type enter on step 0 -> Crashed: stoi
	- Crash when entering any other string by exact challenge name
		- What would you expect to enter to the question
			- Step 3: Please type in the challenge ID from the following challenges
			- Email
- NDNCert Server
	- Crash when receiving Interest with incorrect sha256-params
		- Discovered by GSoC student earlier:  https://redmine.named-data.net/issues/4982
	- Crash on invalid input
		- wrong request, incorrect encryption, missing blocks in parameters TLV, anything non-conformant.

Critical Unimplemented Things
- Hkdf derived key not used
	- In both client and server code, m_aesKey being initialized and derived using hkdf function, but
not actually used anywhere
- PROBE not implemented
	- Probe function is neither fully documented (as a spec) nor implemented anywhere in the server
code. The code only inlcude functionality to set a "handler", but no uses of that (except the test cases).
	- Effectively, it is not hard-coded to return randomly generated number as identity.

Ohter (Unexpected) Things
- Loca-ndncert-anchor not used
	- m_localNdncertAnchor (local-ndncert-anchor)
- Client tool asks for email twice (?!?)
- Why json for NEW/and other exchanges requires `"\n"` at the end ?!?
	- Not having it crashes the server
- Minor: JSON_CA_EQUEST_ID -> typo

**Future work: (Roadblocks to Domination)**
- Problems ralted to encryption/decryption
- Stuck with decrypting JSON:
	- IV, payload, algorithm seem to be the same outputted in Python and received in C++, but C++
crashed with a mystery error from `security::transform::blockCipher`.










































