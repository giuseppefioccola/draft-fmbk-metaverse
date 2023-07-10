---
title: Metaverse impacts on the Internet technologies
abbrev: Metaverse
docname: draft-fmbk-icnrg-metaverse-latest
date: {DATE}
category: info

ipr: trust200902
area: Transport
workgroup:
keyword: Internet-Draft
submissionType: IETF

stand_alone: yes
pi:
  rfcedstyle: yes
  toc: yes
  tocdepth: 6
  tocindent: yes
  sortrefs: yes
  symrefs: yes
  strict: yes
  comments: yes
  compact: yes
  inline: yes
  text-list-symbols: -o*+

author:
  -
    ins: G. Fioccola
    name: Giuseppe Fioccola
    org: Huawei Technologies
    street: Palazzo Verrocchio, Centro Direzionale Milano 2
    city: Segrate (Milan)
    code: 20054
    country: Italy
    email: giuseppe.fioccola@huawei.com
  -
    ins: P. Mendes
    name: Paulo Mendes
    org: Airbus
    city: Taufkirchen
    code: 82024
    country: Germany
    email: paulo.mendes@airbus.com
  -
    ins: J. Burke
    name: Jeff Burke
    org: UCLA REMAP
    street: 102 East Melnitz Hall
    city: Los Angeles
    code: CA  90095
    country: USA
    email: jburke@remap.ucla.edu
  -
    ins: D. Kutscher
    name: Dirk Kutscher
    org: HKUST(GZ)
    city: Guangzhou
    country: China
    email: ietf@dkutscher.net


normative:

informative:

  IEEE-P2874:
     target: https://standards.ieee.org/ieee/2874/10375/
     title: IEEE SA P2874 Standard for Spatial Web Protocol, Architecture and Governance

--- abstract

This document aims to explore the new challenges for the transport network
brought by the development of Metaverse.
It discusses the Metaverse as an Information-Centric Network (ICN).

--- middle

# Introduction

The Web today essentially represents a data-centric application layer:
data named by URLs is manipulated with Representational State Transfer (REST)
primitives. However, the semantic gap with the underlying host-oriented
transport is significant.

The interest in “the Metaverse” suggests that the end-user experience
of the Web will evolve towards an always-on eXtended Reality (XR).
Metaverse introduces the concept of a persistent virtual space of
everyday life as platform-agnostic digital space. It is an interconnected
and limitless virtual world populated by an extension of physical identities,
a digital twin of the physical world.
Metaverse can be seen as the 3D generation of the Internet accessible via
new non-intrusive interfaces (e.g. holographics) and making use of new types
of information (e.g. haptic, temperature, smell, emotions, digital transactions)
that can be exchanged between people, simulated users, and cyber-physical
systems, while preserving data privacy.

Metaverse can also be seen as the next generation of Internet, that can be built
based on Web 3.0. The Web 3.0 is an idea for a new iteration of the World Wide Web
which incorporates concepts such as decentralization, trustworthy interactions,
peer-to-peer, data distribution, decentralized identifiers. This is something
more and different from the vision of Metaverse as full Virtual Reality (VR) and
Augmented Reality (AR).

For this reason, the Metaverse should be considered not as an application
of the current network, but an evolution of the network itself,
reducing rather than widening the gap between network architecture
and application semantics.

The ICN architecture is discussed in this document since it allows to achieve
the integration of application and network layers with less overhead, low latency,
better security, and more disruption tolerance suitable to diverse uses cases.

# Requirements

{{?I-D.han-iccrg-arvr-transport-problem}} started to analyze the requirements of
VR and AR to networking, especially to transport protocol.
As emerging technology, the Metaverse brings up a lot of challenges to technologies
such as information display, image processing, fast computing and networking.
Some of the requirements are:

* Low latency and High-Speed transport to reach services in one-hop and for real-time
  user interactions
* Intelligent control and SLA real-time monitoring to convey the traffic and manage
  network resources and source/route reselection
* Decentralization and Edge Services by positioning the data close to the user
* Reducing data sizes through resolution changes, compression, and more efficient
  encodings


# Gap Analysis

It is known that HTML and HTTP are used to locate a web address, but they do not
provide a sufficient technological foundation for the disparate technologies of
the Web 3.0. In this regard, the HyperSpace Transaction Protocol (HSTP), as
described by {{IEEE-P2874}}, is an evolution of HTTP to connect Metaverse spaces,
including all data and entities (e.g. physical people, cities, buildings, objects,
and their digital twins). It should be able to enable a fully augmented experience,
bridging Web 3.0 technologies, artificial intelligence, blended realities (digital
and physical), and distributed ledger technologies. Similarly, HTML would evolve
in the direction of something like HyperSpace Modeling Language (HSML).

Looking at the transport and network layer, there are the same gaps which needs to
be overcame too. There are elaborate solutions for dealing with bandwidth limitations,
network congestion, lossy transport protocols, and the ever growing size of video data,
to address the above requirements, for instance:

* MPTCP{{?RFC8684}} and MPQUIC{{?I-D.ietf-quic-multipath}} are the expansions of
  TCP{{?RFC9293}} and QUIC{{?RFC9000}} in order to dispatch packets over multiple paths
  to maximize throughput.

* Dynamic Adaptive Streaming over HTTP (DASH) aim to improve the viewport quality
  of immersive videos by refining the tiles delivery. But client-driven nature of DASH
  introduces less control on the server side.

* Media over QUIC (MoQ) ({{?I-D.ietf-moq-requirements}}) and extensions such as QuicR
  ({{?I-D.jennings-moq-proto}}) use similar concepts and delivery mechanisms to those
  used by CDN and named objects.
  There are fundamental characteristics that QuicR provides for ultra low latency delivery,
  by leveraging the characteristics of QUIC protocol.

* The APplication-aware Networking (APN) aims to develop a framework to enable
  fine-granularity network service provisioning (traffic operations) within the
  network domain(s) that supports APN ({{?I-D.li-apn-framework}}). APN aims to use
  the ability to apply policies to traffic flows entering into the infrastructure.
  In modern networks, where things such as deterministic networking and networking
  slicing are required, there is a requirement for more functionality than QoS can
  provide.

* The Computing-Aware Traffic Steering (CATS) aims to analyze the problem on the
  edge node, which makes a decision based on the metrics of interest, and then
  steers the traffic to a node that serves a service instance. Indeed, for AR/VR
  services, the performance experienced by the end users depends on both network
  metrics such as bandwidth and latency, and compute metrics such as processing,
  storage capabilities, and capacity.

In all of these approaches, the Metaverse is considered as an overlay application
with corresponding infrastructure dependencies, but this increases the current gaps
(and resulting costs and technical complexity) between distributed applications and
the underlying network architecture.

Additionally, it is important to understand which networking technology can be aligned
with HSTP {{IEEE-P2874}}. Given that the current Internet stack is host driven, it is
misaligned with the application layer that is data driven.

# Solution with an ICN approach

The Information-Centric Networking (ICN) introduces named information objects,
e.g. media contents, as the central concept as opposed to a physical computer,
or node ({{?RFC7927}}). In ICN approaches, the principal paradigm is not
host-to-host communication as in the current Internet architecture.
The increasing demand for highly scalable and efficient distribution of content
has motivated the development of architectures that focus on information objects,
their properties, and receiver interest in the network to achieve efficient and
reliable distribution of such objects.

Therefore, for the Metaverse, it would be better to assume information-centric system
where most applications participate in granular 3D content exchange, context-aware
integration with the physical world, and other Metaverse-relevant services.
The assumption is that the Metaverse is an information-centric concept that will become
synonymous with the network itself.

## Technical challenges

Many applications already work with data-oriented paradigms. Mapping them to a
host-centric network model creates complexities and robustness issues, which can
be addressed with an ICN oriented approach.

The overlay approach to deal with real-time interactive media adds significant
complexity. It is needed a fine-grained, hierarchical media exchange for low-latency
interactive communication that enables scalable multi-destination distribution,
and in-network replication and transformation that exposes object hierarchy for
fine grained access and security.

Since the Metaverse is an extension of the Web into immersive XR modalities
that are often aligned with physical space, leveraging ICN concepts provides
support for decentralized publishing, content interoperability and co-existence,
based on general building blocks and not within separated application silos as
today’s initial prototypes.

There are four ICN capabilities critical to Metaverse concepts:

* scalable and robust multi-destination communication, overcoming IP multicast
  challenges such as inter-domain routing, scalability, and routing communication
  overhead;

* leveraging wireless broadcast to support shared local views and low-latency
  interactivity;

* privacy, selective attention, content filtering, and autonomous interactions,
  as well as ownership and control on the publishing side;

* supporting in-network processing for objects replication and transformation.

In addition, the interoperability aspects also need to be investigated,
and, for example, Hybrid Information-Centric Networking (hICN), which
implements information-networking functionalities into IPv6
({{?I-D.muscariello-intarea-hicn}}, can provide a solution.

It would be theoretically possible to leverage the solutions mentioned in the
previous section in order to reach the above ICN oriented capabilities. But a
systemic approach would be highly desirable in the longer term.

# Security Considerations

TBD

# IANA Considerations

This document makes no request of IANA.

# Contributors

TBD

# Acknowledgements

TBD
