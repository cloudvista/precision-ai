
## Full-Fidelity VISTA data in Modern Mainstream Cloud-Native Database for Precision AI and Analytics


![cloud analytics overview](img/cloudvista-precision-AI.png)


### Background


The VHA Information Systems Technology and Architecture (VISTA) is the integrated lifelong healthcare delivery system designed and built by VA to support the clinical, business, and financial operations of the VHA. VISTA’s database contains over  300 million veteran-years of data spanning over 35 years and continues to grow at the rate of over four million new lab tests, documents, and images each day. VHA has published over 35,000 peer reviewed medical studies over the past decade based on VISTA data, enabling the VHA to provide the highest quality evidence-based healthcare in the United States.

VISTA’s VA-designed and developed database is a hierachical file store called VA Fileman (File Manager). VA Fileman contains over 6,000 files and 75,000 fields with cross-references and pointers connecting all of these files and fields in a well-defined data model. In present day terms, VA Fileman would be classified as a Document database, for which there are several commercial off-the-shelf versions available (MongoDB, DocumentDB, and others).

### Problem statement

VA Fileman is the operational database of VHA. It is optimized for transaction processing, performance, and reliability for veteran care. Each day Fileman enables 350,000 staff perform over 200 million transactions with sub-second latency and 99.999996% uptime (six-sigma reliability). Fileman is indexed on a per-patient basis and optimized for performance for the clinical staff to provide veteran care. Fileman is not indexed or designed for research, analytics, or population queries.

Over the years, VA has developed several mechanisms to extract subsets of FileMan data for secondary use and analytics, but there is no comprehensive mechanism to export, query, and manage all FileMan data.  Only a relatively small subset of FileMan's operational data is accessible to analytical systems, creating blind spots that may affect the quality of research, trustworthiness of AI models, and accuracy of clinical decision support systems.

A comprehensive approach is thus needed to provide full-fidelity access to VISTA data for interfacing, integration, and syndication of VISTA data with new cloud-native reporting and research systems, and to support full-fidelity machine learning, analytics, and clinical decision support. A modern, mainstream, commercially maintainable database for VISTA data is also necessary for VA to meet VHA data governance mandate, which requires VHA to store all veterans health data in digital form for 75 years.

### Proposal

Comprehensive extraction of VA Fileman  into a modern mainstream cloud-native database of the identical form (document database), preserving all Fileman data and nuance (all files, all fields, all pointers, all cross reference, all metadata) 

This will allow comprehensive access,  management, and query of all Veteran health data in a modern mainstream commercially-supported cloud-native database via unified modern APIs, making all VISTA data comprehensively available to all VA analytical systems  in the VA Enterprise Cloud. (Figure 1).

A full, detailed report of all VISTA data migrated would be generated from the DocumentDB replica to enable planning and scoping of data management for VA.  The report would contrast the FileMan data of each VISTA with the others.  The mechanisms used to make all the reports will serve as examples for how the DocumentDB replica may easily be queried and processed in other projects going forward using the standard MongoDB tools, interfaces, and technology.


###  VISTA Cloud-native Document Database
Criteria | VA Fileman database |  Cloud-native database
--- | --- | ---
Function | Operations | Analtyics
Contents | All VistA data [1] | All VistA data + refinements
Database Model| Fileman Schema | VistA Data Model (FileMan Schema Enhanced)
Where | VistA | VA Enterprise Cloud 
Support | VA-proprietary  | Commodity, commercial, mainstream
Indexing | Rigid; per-patient | Flexible; population
Access | Restricted to Operations [2] | Limited only to facilities of VAEC
Access mechanism | legacy, proprietary interfaces | modern cloud-native API
Governance | Operations focused | Analytics focused
Data management | Minimal; inadequate tools  | Allows distinction of Clinical, Business and Operational data

[1] All Vista data means  
[2] VA Fileman is not designed for nor does it permit analytics workloads; it is designed as the operational database of VHA, and is optimized for performance and reliability.  VA Fileman enables 350,000 staff perform over 200 million transactions each day with sub-second latency and 99.999996% uptime (six sigma reliability).

### Benefits

DocumentDB-based FileMan data provides comprehensive access to all Veteran data directly, securely, with full granularity and data definition of FileMan, but without any of the legacy code or infrastructure to maintain. 

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

Such a direct, full-fidelity (1:1) extraction of all components of FileMan (metadta, indexes, pointers, data model) to a modern database of the identical form (i.e.  document database) will avoid the data loss involved with transforming the data into a different kind of data model(relational or otherwise). 

Full-fidelity replication will comprehensively capture, describe and ‘liberate’ all FileMan data in a modern, maintainable, mainstream database and allow comprehensive access with commodity tools.  VA has developed this automated  FileMan data model migration tool and this is available to the government at no cost. Expertise in FileMan will nevertheless still be required to execute this replication strategy.

What full-fidelity FileMan-DocumentDB replication is not:  
* Not a generic process: No commercial tool or data platform has this capability.
* Not a proprietary process: No vendor-proprietary tools or technology involved.
* Not a  lift-and-shift process: Moving databases to a new datacenter does not fix data accessibility.
* Not an  extract-transform-load (ETL) process: ETL requires extracting subsets of Fileman's data and transforming this so it can 'fit' into a completely different database, with associated loss of metadata, indexes, pointers, and data.  
  

### References

●	VA FileMan Documentation:  https://www.va.gov/vdl/application.asp?appid=5  
●	FileMan model management: https://github.com/cloudvista/master-data-managment
