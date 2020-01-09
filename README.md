# Supply Chain Quality
Supply Chain Quality is an open source community that creates standards and tools for managing artifacts within a supply chain.

## Supply Chain
A supply chain is a system of participants (organizations, people and technology) involved in managing artifacts (products and services) as they move from producers to consumers.

## Artifact
An artifact is a product or service produced or consumed within in a supply chain. Examples of artifacts include the following:

* Physical goods, e.g. hardware
* Digital goods, e.g. software
* Assurances, e.g. logs or certificates assuring artifact quality
* Services, e.g. personal or professional services

## Metadata
Metadata is information about artifacts that allows artifacts to be managed. Examples of metadata include the following:

* Identity - allows unambiguous referral to an artifact, e.g. to facilitate purchase, receipt, transfer, inventory, obsolescense, revocation, customer feedback and association.
* Authenticity - allows validation that artifacts are provided by expected providers.
* Creation - allows validation that artifacts are not tampered with during creation.
* Transmission - allows validation that artifacts are not tampered with prior to use.
* Licensing - allows validation that artifacts conform to licensing requirements. 
* Assurance - allows validation that artifacts conform to product, business and regulatory requirements.

## Scenarios

* Providers are the organizations that make software available for end users to  - specify requirements 
Operating System Providers - 
* Systems Administrators - 
* Product Managers - 
* Business Managers
* Legal Managers - 
* Security Managers - 
* Quality Managers
* Regulatory Managers
* Release Managers - 
* Auditors - 
* Developers - produce software that meets product, business, licensing, security, quality and regulatory requirements.
* End Users - browse, install, update, and run software in accordance to license, security, quality, and regulatory requirements across operating systems and platforms including very small devices, phones, tablets, laptops, desktops, servers, and cloud applications.


## Definitions

Key concepts in the Supply Chain Framework include producers, consumers, artifacts, metadata, authentication authorities, artifact stores, metadata stores, policy, and metadata clients.

### Producers

Producers produce software artifacts and artifact metadata. To assist in the retrieval and validation of artifacts and metadata, producers provide artifact stores, metadata stores and authentication authorities. 


### Consumers

Consumers consume artifacts and metadata. They write policy describing the attributes of artifacts they are willing to consume. In the process of consuming artifacts, they use inspect artifacts using metadata, and they enforce policy. Consumers can also be producers.


### Artifacts

Artifacts are components of software, from small to large. Examples of artifacts include the following:

*   Bytes - e.g. a function of code, data in a database
*   Snippet - a byte range in a file
*   File - e.g. a source or binary
*   Package - a grouping of files
*   Package repository - a grouping of packages
*   Container - a grouping of packages and files
*   Cloud Service - a grouping of containers, packages and files
*   Installed Systems – a grouping of packages and files
*   Hardware(?)


### Metadata

Metadata is information that describes artifacts. Examples of information stored in metadata include the following:

*   Identity (name, producer, version, hash)
*   Authenticity (cryptographic signatures)
*   Build information (tools, environment, configuration)
*   Intellectual property information (license)
*   Relationships with other artifacts (describes, contains)

The format for describing metadata is known as a metadata schema, model or specification.

Examples of metadata specifications today include the following:

*   Grafaes [notes](https://github.com/grafeas/grafeas/blob/master/docs/grafeas_concepts.md#notes)
*   In-toto [link metadata](https://github.com/in-toto/docs/blob/master/in-toto-spec.md)
*   SPDX [2.1](https://spdx.org/spdx-specification-21-web-version)
*   CycloneDX [SBOM](https://cyclonedx.org/)
*   SWID

### Signing Services

Signing services allow consumers to validate that artifacts and metadata come from expected producers. 



*   Signs Metadata
*   Manages distribution, revocation, and replacement of cryptographic keys

Examples today include:



*   The Update Framework ([TUF](https://github.com/theupdateframework/specification/blob/master/tuf-spec.md#the-update-framework-specification))

Examples of authentication authorities include the following:



*   Public Key Infrastructure (PKI) Authorities
*   Web of Trust


### Artifact Stores

Artifact stores distribute artifacts.

Examples of artifact stores today include the following:



*   Object Stores
*   Web Servers
*   Source code repositories
*   Container registries
*   Package repositories
*   Artifact management systems
*   Other (e.g. physical media)

Examples for specifications for describing artifact stores today include the following:



*   RPM package repositories
*   Debian package repositories
*   The Update Framework ([TUF](https://github.com/theupdateframework/specification/blob/master/tuf-spec.md#the-update-framework-specification))
*   Docker container registries (based on TUF)
*   Automotive update repositories ([Uptane](https://uptane.github.io/) - based on TUF)


### Metadata Stores

Metadata stores distribute artifact metadata. Metadata stores may be as simple as a single SBOM document. Metadata stores may also be artifact stores. They are responsible for the following tasks:



*   Stores signed metadata
*   Querying metadata (within and across artifacts)
*   Distributing metadata

Examples of metadata stores today include the following:



*   A single SBOM file
*   Source code repositories
*   Container registries
*   Package repositories
*   Software Heritage
*   Clearly Defined repositories
*   Installed package databases
*   Metadata stores (e.g Grafeas reference implementation)
*   Openstack Artifact Repository
*   Golang transparency

Metadata store specifications today



*   RPM package repository API
*   Debian package repository API
*   [TUF Specification](https://github.com/theupdateframework/specification/blob/master/tuf-spec.md) (implementations - Datadog, Docker Notary, Amazon, Uptane, PyPI)
*   [Grafeas Artifact Metadata API](https://github.com/Grafeas/Grafeas)


### Policy

Policy describes requirements for artifact consumption, including the following:



*   Allowed producers
*   Allowed licenses
*   Allowed build environments and configurations
*   Required security steps (e.g. scanning)
*   Required certifications (e.g. SDL, industry audits)
*   Expected order of steps in the chain (e.g. to prevent man in the middle attacks)

Examples of policy specifications today:



*   In-toto sub-layout
*   [Kritis](https://github.com/grafeas/kritis) policy specification for Kubernetes applications

Examples of policy implementations today:



*   [Rego](https://www.openpolicyagent.org/docs/latest/policy-language/) (part of Open Policy Agent - OPA)
*   Kritis [reference implementation](https://github.com/grafeas/kritis/blob/master/docs/install.md) (against Google Cloud Container Analysis API)
*   Linux build system (internal policies)


### Metadata Clients

Metadata clients query metadata stores to receive and process metadata. They may also obtain and inspect artifacts and enforce policy.

Metadata clients query metadata stores to receive information such as the following:



*   Lists of artifacts available
*   Lists of artifacts containing specific metadata values
*   Metadata values across multiple artifacts
*   Metadata values for specific artifacts

(Question - which of these does the Software Bill of Materials specification cover?)

Metadata clients may handle policy validation and enforcement including the following:



*   Signature verification
*   Artifact hash validation
*   License validation
*   Build/build environment validation (e.g. reproducible build)
*   Required steps validation
*   Required certification validation

Examples of metadata client implementations today



*   [Open Policy Agent](https://www.openpolicyagent.org/docs/latest/) (OPA)
*   [Grafeas client libraries](https://github.com/grafeas) - including [Kritis](https://www.bing.com/search?q=grafeas+kritis&PC=U531&cvid=e7f41d082a614612b1ffb6c22bf66ae2&FORM=ANNTA9) (admission controller)
*   [In-toto](https://github.com/in-toto/in-toto) verify (admission controller)
*   [The Update Framework](https://github.com/theupdateframework/specification/blob/master/tuf-spec.md) (TUF)-based clients
    *   

