
## Full-Fidelity VISTA data in Modern Mainstream Cloud-Native Database for Precision AI and Analytics

### Overview
![cloud analytics overview](img/cloudvista-precision-ai.png)


### Background


The VHA Information Systems Technology and Architecture (VISTA) is the comprehensive lifelong healthcare delivery system of the VA designed and built to support the clinical, business, and financial operations of the VHA. VISTA’s database contains over  300 million veteran-years of data spanning over 35 years and continues to grow at the rate of over four million new lab tests, documents, and images each day. VHA has published over 35,000 peer reviewed medical studies over the past decade based on VISTA data, enabling the VHA to provide the highest quality evidence-based healthcare in the United States.

VISTA’s database is VA-designed and developed and is called VA Fileman.  VA FileMan is a hierachical file store, and contains over 6,000 files and 75,000 fields with cross-references and pointers connecting all of these files and fields in a well-defined data model. In present day terms, VA Fileman would be classified as a Document database, for which there are several commercial examples (MongoDB, DocumentDB, and others).

### Problem statement

Fileman is the operational database of VHA. It is optimized for transaction processing, performance, and reliability for veteran care. Each day Fileman supports 350,000 staff perform over 200 million transactions with millisecond latency and 99.999996% uptime (six sigma reliability). Fileman is indexed on a per-patient basis to optimize the performance of the clinical staff for veteran care; it is not indexed or designed for research, analytics, or population queries.

Over the years, VA has developed several mechanisms to extract subsets of FileMan data for secondary use and analytics, but there is no comprehensive mechanism to export, query, and manage all FileMan data.  Currently only a small subset of FileMan data is accessible to analytical systems, creating blind spots that affect the quality of research, trustworthiness of AI models, and accuracy clinical decision support systems.

A comprehensive approach is thus needed to provide full-fidelity access to VISTA data for interfacing, integration, and syndication of VISTA data with new cloud-native reporting and research systems, and to support full-fidelity machine learning, analytics, and clinical decision support. Finally, a portable mainstream database is required by VA to meet VHA data governance mandates to preserve veteran health data in digital computable form for 75 years.

### Proposal

Extraction of VISTA’s database (VA FileMan) with full fidelity (all of the data, with full granularity of all files and fields) into a modern  commercially-supported  cloud-native database of the same form (document database) in the VA Enterprise Cloud. This will allow comprehensive continuity of access, management, and query of all Veteran health data in a modern, mainstream, maintainable, cloud-native database, and connect easily via modern APIs to the many VA analytical systems that are also hosted in the VA Enterprise Cloud. (Figure 1).

A full, detailed report of all VISTA data migrated would be generated from the VISTA MongoDB replica to enable planning and scoping of data management for VA.  The report would contrast the FileMan data of each VISTA with the others.  The mechanisms used to make all the reports will serve as examples for how the MongoDB replica may easily be queried and processed in other projects going forward using the standard MongoDB tools, interfaces, and technology.


###  VISTA Cloud-native Document Database
Criteria | VA Fileman database|  Cloud-native database
--- | --- | ---
Database Model | Document DB | Document DB
Contents | All VistA data | All VistA data + refinements
Where | VistA | VA Enterprise Cloud 
Support | VA-internal  (bespoke, proprietary)  | Commercial (mainstream, commodity )
Indexing | Per Patient (rigid) | Population (flexible, adaptable)
Model| Fileman Schema (data dictionary) | VistA Data Model (FileMan Schema Enhanced)
Access | Restricted to Operations* | As much as VAEC facilities allow
Governance | Operations focused | Analytics focused, distinction of Clinical, Business and Operational data

* VA Fileman is neither designed for nor does it permit analytics workloads; it is designed as the operational database of VHA, and is optimized for performance and reliability.  VA Fileman supports 350,000 staff perform over 200 million transactions each day with sub-second latency and 99.999996% uptime (six sigma reliability).

### Benefits

MongoDB-based FileMan data provides comprehensive access to all Veteran data directly, securely, with full granularity and data definition of FileMan, but without any of the legacy code or infrastructure to maintain. 

Preserving the FileMan "framing" for data ensures preservation of the semantics of all VISTA data without the requiring a laborious and largely manually created data reframing which could never encompass all the data of a VISTA system in a timely or cost-effective fashion.


### Assumptions

1. __FileMan is a Model__
Pointers, Dates, Types, Cross References, Hierarchy, and Document Mix
2. __One can replicate the FileMan Model with full fidelity in a modern commercial datastore__ 
FileMan-level replication preserves all definition, structure, pointers, and cross-references
3. __A Full-Fidelity FileMan Model Exporter Exists and doesn't need new work.__
This was created under a prior VA project and is available immediately 
4. __Exported FileMan-consistent data fits natively into commercial Document Stores__ 
This includes MongoDB, and Azure- and AWS- managed versions of MongoDB
5. __Replication will be in a FedRAMP-HIGH VA Enterprise Cloud Production Environment__
The full-fidelity replica of FileMan will contain PHI/PII
6.  __VA has capacity in managing MongoDB databases__
VA currently manages a massive MongoDB database farm in the VA Enterprise Cloud


### Technical Note

The direct Fileman-to-DocumentDB extraction is best described as an extract-and-load ("EL") process, rather than an extract-transform-load ("ETL") process. __This direct extract-load process does not involve any transformation, which is precisely why it is lossless and full-fidelity.__

Such a direct, full-fidelity 1:1 extraction of the FileMan data model to a modern database of the identical form (i.e.  document database) will avoid the data loss involved with transforming the data into a different kind of data model(relational or otherwise). 

Full-fidelity direct replication will comprehensively capture, describe and ‘liberate’ all FileMan data in a modern, maintainable, mainstream database will allow comprehensive access with commity tools.  VA has developed this automated  FileMan data model migration tool and this is available to the government at no cost. Expertise in FileMan will nevertheless still be required to execute this replication strategy.

What full-fidelity FileMan-MongoDB replication is not:  
* Not a generic process:: No commercial tool or data platform has this capability.
* Not a proprietary process:: No vendor-proprietary tools or technology involved.
* Not a  lift-and-shift process:: Moving databases to a new datacenter does not fix data accessibility.
* Not an  extract-transform-load (ETL) process:  ETL requires extracting subsets of Fileman's data and transforming this so it can 'fit' into a completely different database, with associated loss of metadata, indexes, pointers, and data.  
  
  
  This is an extract-load (EL) process which does not involve any transformation, and is the reason it is lossless and full-fidelity representation of Fileman data.


### References

●	VA FileMan Documentation:  https://www.va.gov/vdl/application.asp?appid=5  
●	FileMan model management: https://github.com/cloudvista/master-data-managment
