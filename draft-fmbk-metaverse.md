---
title: Metaverse impacts on the Internet technologies
abbrev: Metaverse
docname: draft-fmbk-metaverse-latest
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
  TCP: RFC9293
  QUIC: RFC9000
  MPTCP: RFC8684
  MPQUIC: I-D.ietf-quic-multipath


--- abstract

This document aims to explore the new challenges for the transport network
brought by the development of Metaverse.
It will also cover requirements, gap analysis and solutions.

--- middle

# Introduction

Metaverse introduces the concept of a persistent virtual space of everyday life
as platform-agnostic digital space. It is an interconnected and limitless virtual
world populated by an extension of physical identities, a digital twin of the
physical world.

Metaverse can be defined as the 3D generation of the Internet accessible via
new non-intrusive interfaces (e.g. holographics) and making use of new types
of information (e.g. haptic, temperature, smell, emotions, digital transactions)
that can be exchanged between people, simulated users, and cyber-physical
systems, while preserving data privacy.

Virtual Reality (VR) and Augmented Reality (AR) technologies have enormous
potential in many different fields.
Cloud based AR/VR are evolving since AR/VR applications combine high bandwidth
demands and high sensitivity to latency and dropped packets.
There are elaborate solutions for dealing with bandwidth limitations, network
congestion, lossy transport protocols, and the ever growing size of video data,
for instance:

* {{MPTCP}} and {{MPQUIC}} are the expansions of {{TCP}} and {{QUIC}} in order to
  dispatch packets over multiple paths to maximize throughput.
* Adaptive Streaming approaches based on HTTP/2 aim to improve the viewport quality
  of immersive videos by refining the tiles delivery.

But these solutions have limitations when we consider their application to the
Metaverse virtual space.

# Requirements

{{?I-D.han-iccrg-arvr-transport-problem}} started to analyze the requirements of
VR and AR to networking, especially to transport protocol.
As emerging technology, VR and AR bring up a lot of challenges to technologies
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

Dynamic Adaptive Streaming over HTTP (DASH) is an adaptive bitrate streaming
technique that enables high quality streaming of media content over HTTP.
Typically, the DASH client adaptively requests small chunks of media based on
the available bandwidth and other resources. This client-pull technology has
proven to be more flexible, firewall-friendly, and CDN scalable than server-push
technologies. However, there is less control given the decentralized and
client-driven nature of DASH, which introduces new challenges for them to offer
a consistent and possibly higher quality of service for the new Metaverse
experience.

The Metaverse immersive space require intensive computational resources to render
and display the video frames in a short motion-to-photon time so that people can
obtain a real-time experience.
VR and AR on the Edge Cloud is becoming a promising technique, which enables
users to play high quality VR games without equipping high end gaming PCs.

With Metaverse, it is expected that a big amount of data can be exchanged between
autonomous networks over untrusted channels. To ensure security, privacy, and
trust among stakeholders, Blockchain can be employed to allow intelligent resource
management, user access control, audibility, and chronology in stored transactions.

# Solutions

Some initiatives are already dealing with related issues in IETF:

* Network of Information defines an Information-Centric Networking (ICN) with named
  “information objects”, e.g. media contents, as the central concept as opposed to
  a physical computer, or "node".
  In ICN approaches, the principal paradigm is not host-to-host communication as in
  the current Internet architecture ({{?RFC7927}}).
  The increasing demand for highly scalable and efficient distribution of content
  has motivated the development of architectures that focus on information objects,
  their properties, and receiver interest in the network to achieve efficient and
  reliable distribution of such objects.

* QuicR defines a Media Delivery Protocol over QUIC and its architecture
  {{?I-D.jennings-moq-quicr-arch}} uses similar concepts and delivery mechanisms to
  those used by CDN and named objects. However there are fundamental
  characteristics that QuicR provides for ultra low latency delivery, by leveraging
  the characteristics of QUIC protocol.

* Low Latency Low Loss Scalable throughput technology (L4S) can significantly reduce
  lag in an interactive cloud-based video game ({{?I-D.ietf-tsvwg-l4s-arch}}).
  L4S relies on ECN (Explicit Congestion Notification) in the IP header to indicate
  queue build-up in the radio access network to the application.

* The APplication-aware Networking (APN) aims to develop a framework to enable
  fine-granularity network service provisioning (traffic operations) within the
  network domain(s) that supports APN ({{?I-D.li-apn-framework}}). APN aims to use
  the ability to apply policies to traffic flows entering into the infrastructure
  (APN domain).
  In modern networks, where things such as deterministic networking and networking
  slicing are required, there is a requirement for more functionality than QoS can
  provide.

* Glass to Glass Internet Ecosystem (GGIE) was presented few years ago and aimed to
  leverage IPv6 Glass to Glass. End to end Internet digital video ecosystem focusing
  on all phases of the video life cycle: Capture-Edit-Package-Distribute-Find-Watch.
  The network is assumed to be IPv6-only. More details can be found in
  {{?I-D.deen-daigle-ggie}}.


# Security Considerations

TBD

# IANA Considerations

This document makes no request of IANA.

# Contributors

TBD

# Acknowledgements

TBD
