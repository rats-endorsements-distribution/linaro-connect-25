# Endorsement API Workshop Report

## Quick Recap
The meeting focused on endorsement and reference value distribution for attestation, covering topics such as creation protocols, existing distribution services, and standardization efforts.
Participants discussed various challenges and potential solutions related to managing endorsements, including versioning, timeliness, and revocation mechanisms.
The group also explored the CoSERV proposal for conveying endorsements and reference values to verifiers, along with its potential implementations and integration with existing systems.

## Meeting Summary

### Confidential Computing Endorsement Distribution Challenges
The meeting begins with introductions from participants, who share their backgrounds and interests in endorsement distribution for attestation.
Paul Howard from Arm introduces the topic, emphasizing the need to address fragmentation risks in endorsement distribution across hardware, software, and firmware.
Attendees include representatives from Linaro, Microsoft, Alibaba Cloud, Huawei, Fujitsu, and other organizations involved in confidential computing and remote attestation.
The group discusses the agenda, which includes talks on endorsement creation protocols, existing distribution services, interaction models and APIs, and standardization efforts.
Michael Richardson is set to present first on the endorsement creation protocol and proof of possession used by auditors.

### Proof of Presence Endorsement Concept
Michael Richardson presents a concept for a "Proof of Presence Endorsement" to verify the physical location of network devices.
This endorsement is created by an auditor who physically inspects the device and exchanges signed data with it through a console protocol.
The process involves the auditor connecting to the device, verifying its identity, and creating a signed attestation about its location and connections.
The endorsement can then be loaded into the device for future verification.
Michael discusses potential implementation details, security considerations, and the relationship of this concept to other standards like MUD (Manufacturer Usage Description).
The group discusses the format of the endorsement (EAR vs. CORIM) and how this fits into the broader attestation model, noting that it's different from manufacturer-provided endorsements and focuses on deployed device characteristics.

### Managing Endorsements in Firmware Updates
The group discusses requirements for managing endorsements in remote attestation, particularly in the context of firmware updates.
Paul explains that endorsements for different firmware versions are distinct and don't overwrite each other.
Shefali raises concerns about scenarios where firmware updates might completely change endorsement values.
The group agrees on the need for standardization in handling endorsement lifecycles and explicit revocation signals.
Jag brings up the challenge of managing endorsements for system topologies that don't have version numbers.
The discussion highlights the complexity of maintaining up-to-date endorsements and the potential for race conditions between attesters and verifiers.
Michael expressed the view that there must always be a version number when attempting to address an endorsement or reference value, because otherwise there is a high degree of ambiguity and scope for race conditions.

### Managing Component Endorsements in Systems
The discussion focuses on the challenges of managing and updating endorsements for components in a system.
Greg outlines a scenario where a component's security status changes over time, and the group explores how to handle this mechanically.
Thomas suggests using a TTL (Time To Live) mechanism similar to DNS, where endorsements have a validity period set by the signer.
The group also discusses the need for different parties in the endorsement flow to have a voice in determining the freshness of endorsements.
Jag points out that the CORIM specification includes a mechanism for replacing or deleting endorsements using the "linked" tag.
The conversation concludes with a discussion about versioning for different types of components, including virtual "shapes" in cloud computing environments.

### Versioning and Timeliness in Endorsements
The discussion focuses on versioning and timeliness of endorsements in attestation systems.
Michael and Greg emphasize the importance of versioning for all components, including topologies and shapes.
They agree that timeliness signals are critical for endorsements, but caution against specifying implementation details like revocation mechanisms in the requirements.
The group discusses strategies for handling endorsement expiration and validity periods, with Thomas suggesting that attestation results should not be limited by the shortest endorsement validity period.
They also touch on the differences between recentness and freshness of endorsements. 

### Conclusions from the Requirements Conversation
- Shefali: endorsements need timeliness/freshness signals (incl. explicit revocation) for statements previously made by the endorser
- Greg: the parties in the flow have a voice to say how fresh the endorsement is (Supply chain vs Repackager — CSP)
- Jag: attester shapes change too, not just the measured component
- Michael: Versions: we need to assign versions to things
Synth: attester shapes are endorsements and must have versions
- Greg’s note: I suspect the designs we come up with for endorsements + distribution API's should enable timeliness mechanisms that are both based on revocation and also short lived endorsements

### Existing Technologies
Paul presents an overview of two existing endorsement distribution technologies: AMD's Key Distribution Service (KDS) and NVIDIA's Reference Integrity Manifest (RIM) service, highlighting their different approaches to providing endorsements and reference values for attestation verification. 
These two technologies were chosen because they are diverse in quite informative ways, making them useful case studies when trying to design industry standards that can flex to different use cases.
The NVIDIA architecture is especially interesting because it demonstrates both models for verification: an online verification service, or a local verifier.
The API for accessing Nvidia's reference integrity manifests (RIMs) is described, including how to enumerate and fetch RIMs in different formats.
The RIM service is used to provide the reference measurements in both cases.
The AMD case is interesting because it demonstrates a situation where the endorsement data varies depending on the TCB of the attester, motivating the need for dynamic query parameters over static URLs for endorsements.

### Nvidia Certificate and Revocation Process
Greg shares detailed information about Nvidia's certificate and revocation process for their attestation system.
The certificates have a 2-year expiry but use OCSP for revocation checking with a 24-hour cache time.
Greg has been monitoring the system and noticed changes in how Nvidia signs different product bundles.
Thomas and Greg discuss the implications of this process for product releases and security updates.

### MUD Applications in Remote Attestation
Henk presents an overview of MUD (Manufacturer Usage Description) and its potential applications in RATS (Remote Attestation Procedures).
He explains that MUD started as a mechanism for adding ad-hoc countermeasures against distributed denial of service attacks but has evolved into a more general discovery mechanism.
Henk suggests that MUD could be used to discover various elements in RATS, such as remote verifiers, updated endorsements, or trust anchor updates.
He proposes that the next steps should focus on determining what exactly needs to be discovered using MUD in the context of RATS.
The discussion then shifts to the importance of considering different roles in the RATS architecture and how they might inform the semantics of MUD usage.
The group also discusses challenges related to updating MUD files and maintaining the chain of trust, particularly in the context of device firmware updates and endorsements.
Thomas discussed the importance of a convenient way across various verticals, emphasizing the key role of the chain of custody.
He also raised questions about the training of conceptual message types or roles and whether duties should be split between multiple MUD modules.

### Standardization in Confidential Computing Discussed
Nicolae presented a discussion on standardization in the area of confidential computing, highlighting the involvement of different standardization bodies such as IETF, industry-led standardization, and the European Telecom Standards Institute (ETSI).
Nicolae also mentioned the ongoing standardization in ISO and the potential challenges and opportunities this presents.
Henk suggested that individuals need to volunteer to take on the task of liaising between these different bodies.
Kathleen agreed with Nicolae's points and suggested that they ignore ISO for now, as it seems to be disconnected from the existing forums.
She also suggested that they align their work with ETSI to cover unique use cases in the telecom industry.

### CoSERV Proposal for Endorsements and Reference Values
The group discusses the CoSERV (Concise Selector for Endorsements and Reference Values) proposal for conveying endorsements and reference values to verifiers.
Paul outlines the guiding principles, including decoupling the message from transport, supporting different interaction models, and optimizing for constrained consumers.
Greg raises a question about supporting legacy data formats, which Thomas acknowledges as important for adoption.
The discussion also covers aggregating endorsements from multiple sources and flexible trust models.
Caching of endorsements is debated, with Greg highlighting challenges around revocation and freshness when caching signed artifacts from external sources.

### Coserve's Role in Endorsement Validation
The discussion focuses on the role and responsibilities of the CoSERV component in handling endorsements and their validation.
Greg raises concerns about whether CoSERV should provide all data required to validate endorsements, including up-to-date OCSP responses for certificate chains.
Thomas clarifies that CoSERV is intended to carry deep audit information from throughout the supply chain, but the current design does not yet specify how this will be done.
The group debates the challenges of managing timeliness and revocation of endorsements, particularly in cases like NVIDIA's approach of tying signing authority to integrity measurements.
They consider the implications of changing OCSP validity periods and how to handle these changes in the CoSERV context.
The conversation concludes with a suggestion to separate concerns between distribution and potential re-signing roles for CoSERV, acknowledging that if coserve takes on additional roles, it could become a trusted third party making derived decisions.

### CoSERV Protocol and Veraison Implementation
Thomas discusses the CoSERV (Endorsement Distribution) protocol, which includes queries and result sets.
The query allows specifying interest in particular types of artifacts (like reference values or trust anchors) for specific attesters.
Query selectors can be based on class, instance, or group.
The result set contains the requested artifacts along with an expiry timestamp.
The artifacts are expressed as triples with their original signing authority.
Thomas mentions they are prototyping this in Veraison, with the implementation mirroring the specification.
Shefali asks about a demo, but Thomas clarifies they plan to describe the proof of concept rather than demonstrate it live.

### CoSERV API and Vendor Implementations
The discussion focuses on the CoSERV API and its potential implementations.
Paul reassures the collective audience that the concept of aggregating and re-signing endorsements is only a potential use case that we would like CoSERV to support.
Aggregation is not an inherent property of CoSERV.
Also, CoSERV is not a component or a role: it is simply a common query/response language that can be supported by endpoints.
Greg seeks clarification on the "North Star" vision for CoSERV, asking if the end goal is for vendors like Intel, AMD, and Nvidia to publish signed CoRIMs online with both batch and fine-grained query APIs.
Thomas confirms this and adds that additional CoSERV layers might be needed in complex supply chains.
The conversation also touches on the challenges of sharing reference measurements across multiple supply chain layers, with Thomas noting that aggregators might need to produce new reference measurements for customers who can't access original manufacturer data.

### NVIDIA Service Prototype API Discussion
Paul reports his hackathon activities from the morning session, looking into how the NVIDIA RIM service would map to CoSERV.
This effort was specifically focused on RIMS that are published in CoRIM format, as opposed to the TCG RIMs in XML format.
Paul walks through a simple, self-contained command-line program that makes a single API call to the RIM service to obtain a CoRIM, and then shows how its inner CoMID and reference value structures could be copied across to simulate a CoSERV query/response transaction.
Thomas points out that he has developed a plug-in framework as part of his PoC efforts in Veraison, and it would be possible to take some of the same code into that framework, allowing Veraison to act as a CoSERV proxy and aggregator for NVIDIA RIMs.
This could become part of a future hackathon, possibly at the forthcoming IETF meeting in Madrid.
Ned asks about how the signatures were being handled, and Paul responds that there is currently no signature handling or re-signing taking place, because this was only a very brief and constrained prototyping exercise.

### CoSERV API and Implementation
The group discusses the CoSERV API and its capability to return signed CoRIM from the original source.
Thomas clarifies that while this functionality is not yet implemented, it is a core requirement to optionally bundle the original data for transparency.
The conversation then shifts to the timeline for implementing CoSERV support in Veraison, with Thomas explaining that it's currently in a branch but not ready for mainline due to the evolving nature of the specification.

### CDDL Data Model for In-ToTo Attestations
Henk reports on his morning hackathon activities.
He provides an overview of In-Toto attestations, explaining their potential use in showing the provenance of reference values in the CoRIM space.
He shares his exploration of the In-Toto attestation specification, noting its similarities to their existing system and the potential for mapping it to their schema, though some challenges remain due to the complexity of certain predicates.

### Actions and Next Steps
- Michael to further develop the endorsement creation protocol for physical audits of device locations.
- Thomas and Michael to determine which working group the endorsement creation protocol document should be submitted to.
- Kathleen to draft a liaison request for ETSI and ISO documents related to confidential computing standards.
- Nicolae to send Kathleen the contact information for the head of the ISO work group on confidential computing.
- Thomas to provide Kathleen with specific document requests for Etsy and ISO.
- Confidential computing community to consider ways to align work in ETSI with IETF use cases.
- Workshop participants to continue discussion on CoSERV and its implementation as a standard for endorsement and reference value conveyance.
- Paul to add a report summarizing the meeting's discussions and outcomes to the project repository.
- Paul to continue working on the example proxy plugin for NVIDIA RIMs in the CoSERV implementation.
- Paul and Thomas to consider adding support for returning original signed CoRIMs as part of the CoSERV API.
- Paul and Thomas to develop deployment scenarios to clarify different use cases for CoSERV.
- Thomas to continue developing the CoSERV proof-of-concept in their project branch.
- Thomas to save the chat log from the meeting.
