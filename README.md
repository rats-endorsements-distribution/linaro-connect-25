# Endorsement API Workshop at [Linaro Connect 2025](https://www.linaro.org/connect)

## Abstract

Endorsements and Reference Values, defined in [RFC9334](https://www.ietf.org/rfc/rfc9334.html), are essential artefacts for attestation evidence appraisal.
They can originate from various sources throughout the supply chain, including silicon manufacturers, hardware integrators, firmware providers, and software providers.
Their distribution is influenced by technical, commercial, and even geopolitical factors.
The potential consumers of these artefacts, referred to as “Verifiers” in RATS terms, include cloud-hosted verification services, local verifiers bundled with relying parties, constrained nodes, and endpoint devices.
This acute diversity creates challenges for software integration and poses fragmentation risks.
Aligning on data formats and APIs will help address these challenges and maximise software component reuse for data transactions between endpoints.

The workshop aims to highlight the issue of endorsement and reference value conveyance within the RATS architecture and to invite collaboration in this area.
We will gather ideas and initiate early consensus building, with the intention of eventually creating or evolving one or more Internet Drafts to enhance the standards landscape surrounding these conveyances.

During the workshop, we will explore in-depth:
* Requirements,
* Existing services and tools,
* Interaction models and APIs,
* Prototyping, and
* Standardisation.

## Schedule

The day's schedule is as follows:
* Morning: Hackathon,
* Afternoon: Presentations and Round-table Discussion.

## Call For Topics

We are soliciting participants to bring their topic for discussion.

You can add one or more items to the agenda by filing an issue:
* [Hackathon project](https://github.com/rats-endorsements-distribution/linaro-connect-25/issues/new?template=hackathon-item.md),
* [Presentations and discussion](https://github.com/rats-endorsements-distribution/linaro-connect-25/issues/new?template=agenda-item.md).

In-scope topics include, but are not limited to, the following:

* Harmonizing CoRIM-based and in-toto-based information and data models
* Existing Endorsement APIs (e.g., NVIDIA RIM Service, AMD Key Distribution System (KDS))
* Endorsement APIs and discovery (e.g., using MUD)
* Publish-subscribe architecture in HTTP and CoAP
* Ongoing prototyping efforts

## Details

May 13 2025, 9am-5pm WEST (GMT+1)

Corinthia, Lisbon, Portugal [(map)](https://www.openstreetmap.org/way/101941942#map=19/38.738712/-9.166492)

Room: TBD

Remote participation: [[Zoom URL]](https://linaro-org.zoom.us/j/92068141447) [[Details]](remote-participation.md)

## Participants

| Name | Organisation | Time zone, if remote |
|--|--|--|
| Paul Howard | Arm | n.a. |
| Thomas Fossati | Linaro | n.a. |
| Greg Kostal | Microsoft Azure | PDT (UTC-7) |
| Ned Smith | Intel | PDT (UTC-7) |
| Kathleen Moriarty | Center for Internet Security | EDT (UTC-4) |
| Michael Richardson | Sandelman Software Works | n.a. |
| A.J. Stein | NIST | EDT (UTC-4) |
| Yogesh Deshpande | Arm | n.a. |
| Mathieu Poirier | Linaro | n.a. |
| Jag Raman | Oracle | EDT (UTC-4) |
| Henk Birkholz | Fraunhofer SIT | n.a. |
| Shefali Kamal | Fujitsu | IST (UTC+05:30) |
| xynnn (Ding) | Alibaba | CST (UTC+8) |
| Nicolae Paladi | CanaryBit | CET |
| Tobin Feldman-Fitzthum | IBM Research | EDT |
| Huang Yang | Huawei | CST (UTC+8) |
| Larry Dewey | AMD | CDT (UTC-5) |
| Jun Zhang | Huawei | CET |

## Agenda

### Morning (Hackathon) Activities

**Note**: On-site participation only.
However, all participants are welcome to engage in hacking/prototyping activities in advance of the event, and present their findings as part of the afternoon activities, where remote participation will be enabled.

Activities can happen in parallel.
Timings are fluid, but activities wind up for lunch circa 12:00 WEST.

| Participating | Activity | Live on site?
|--|--|--|
| Paul Howard, Thomas Fossati | Evolving the CoSERV draft | yes
| Henk Birkholz, Michael Richardson | Tiny Implementation for Muddy RATS | yes
| Henk Birkholz | Prototype CDDL for in-toto Attestations | yes
| Paul Howard | CoSERV proxies for existing services | yes


### Afternoon (Presentation and Discussion) Activities

**Note**: Remote participation is possible.
See above for details.
Timings subject to change on the day.

| Who | Track | Title | Timing (WEST GMT+1) | Links
|--|--|--|--|--|
| Paul Howard, All | N/A | Welcome, Introductions and Agenda-Finalizing | 13:00 | [slides](materials/introduction/intro-v1.pdf)
| Michael Richardson | Requirements | An Endorsement Creation Protocol for Use by Auditors | 13:20 | [abstract](https://github.com/rats-endorsements-distribution/linaro-connect-25/issues/1), [draft](https://github.com/mcr/pop-endorsement/blob/main/pop-endorsement.mkd)
| TBD | Requirements | _other track topics TBD_ | 13:40
| Paul Howard | Existing Technologies | AMD KDS and NVIDIA RIM Service | 14:00 | [slides](materials/existing-technologies/existing-technologies-v1.pdf)
| Henk Birkholz | Interaction Models and APIs | Use of MUD as Service Discovery Mechanism in RATS | 14:20 | [abstract](https://github.com/rats-endorsements-distribution/linaro-connect-25/issues/8), [draft](https://datatracker.ietf.org/doc/draft-birkholz-rats-mud/)
| Nicolae Paladi | Standardisation | IETF, ETSI-NFV and now ISO | 14:50 | [abstract](https://github.com/rats-endorsements-distribution/linaro-connect-25/issues/7)
| Thomas Fossati, Paul Howard | Standardisation | CoSERV - Concise Selector for Endorsements and Reference Values | 15:20 | [draft](https://datatracker.ietf.org/doc/draft-howard-rats-coserv/), [slides](materials/coserv-std/coserv-std-v1.pdf)
| All | N/A | **BREAK** (20 mins) | 15:40
| Thomas Fossati | Prototyping | CoSERV PoC in Veraison | 16:00 | [slides](materials/coserv-poc/coserv-poc-v1.pdf)
| All Hackathon Participants | Prototyping | Round-the-table reporting and discussion | 16:15
| Paul Howard, All | N/A | Wrap-Up | 17:30
| | | | |

## Report

TODO
