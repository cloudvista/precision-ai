
## Code-driven VISTA vs Model-driven VISTA

Code-driven VISTA <br> (Current) | Model-driven VISTA <br> (VISTA Data Project)
---|---
__Current interfacing  to VISTA is through thousands (5500+) of unique, opaque, one-way  (either read or write)  legacy (20+ years old)  MUMPS remote procedure calls (RPCs) which are neither documented nor maintained.__ These are hard-coded in MUMPS for specific clients only and not interchangeable to other clients due to business logic within the custom MUMPS and client code. |   __All interfacing to VISTA is through one single, secure, symmetric (bidirectional)  read-write Master VISTA Data Model (MVDM).__  The read data model is identical to the write data model (i.e. symmetric)  providing one single universal structured data read/write mechanism. 
__Access is based on the legacy (1980's) terminal interface and its Menu Actions.__ This is a nonstandard, bespoke, opaque mechanism hardcoded to a legacy terminal interface and its 9000+ menu options within 1700 menus. Clearly this is not applicable to any new, modern, web, mobile, or graphical interfaces.  The only way to interface to data currently is to write new MUMPS code using the opaque Terminal-specific Actions-centric security, in addition to custom RPC MUMPS security code. | __New, modern, industry-standard, fine-grained access control__ is provided through patient-centric access control (PCAC; new blue layer).  All existing RPC-based clients (left) access the MVDM via the __RPC Emulator__, an RPC isolation and audit security layer (new). All new clients and integrations (right) access the MVDM via PCAC security. Authentication (top layer) will leverage enterprise identity and authentication management with time-limited SAML tokens.  
__Many of the MUMPS RPCs bypass the Fileman API and Data Dictionary, writing direct to MUMPS global storage.__ Bypassing the Fileman API means that the security and auditing measures of  the database are bypassed, creating a significant security gap, in addition to corrupted data dictionary.  This makes the data inaccessible to any other applications or by any other method other than by writing yet more custom MUMPS global data access code. | __All  interfaces and functionality are Model-driven,  language-agnostic, client-agnostic, and Fileman API compliant, assuring universal auditing of all data access.__ 


<br>


Interface |  Code-driven VISTA <br>MUMPS RPCs (x5500)  | Model-driven VISTA<br>Master VISTA Data Model (x1)
--- | --- | ---
Method |   :no_entry_sign:  Relies on over 5500 client-specific, non-interchangeable legacy MUMPS routines <br>  :no_entry_sign: Distinct, unique routines for reading vs writing the same data <br>  :no_entry_sign: Requires extensive knowledge and experience with MUMPS and VISTA | :white_check_mark:  Data Model-Driven :new: <br> :white_check_mark: Client-agnostic :new: <br> :white_check_mark: One single, symmetric read-write mechanism for all data :new: <br>:white_check_mark: Requires no knowledge or experience with VISTA internals or MUMPS.
Ease of interfacing to new clients | :no_entry_sign: HARD | :white_check_mark: EASY
Security |  :no_entry_sign: Patchy, Opaque  | :white_check_mark:  Comprehensive, Clear
Authentication |  Kernel Access/Verify | :white_check_mark: SAML token
Access Control |  :no_entry_sign: Dependent on and specific to the legacy terminal interface Menu Options  | :white_check_mark:  Applicable to any and all (new) interfaces  <br>:white_check_mark:  Data-Centric; :new: <br> :white_check_mark:  Patient-Centric :new: <br>:white_check_mark:   Enables Attribute-Based Access Control (ABAC) :new:
Fileman API Compliant|  :no_entry_sign: Unreliable, Incomplete <br> :no_entry_sign: Variable compliance| :white_check_mark:  Reliable, Complete <br> :white_check_mark: 100% Compliant
Audit |   :no_entry_sign: Incomplete <br> :no_entry_sign: Bypassess Fileman auditing | :white_check_mark:  Comprehensive AND <br> :white_check_mark: Patient-Centric :new:  
Unit Tested  |   :no_entry_sign: NO <br>  :no_entry_sign:  0% logic tested  | :white_check_mark: YES <br> :white_check_mark: 100% logic validated
Documentation |  :no_entry_sign: Incomplete, inconsistent, unclear. <br> :no_entry_sign:  Requires understanding MUMPS code | :white_check_mark: Complete, consistent, clear.  <br>:white_check_mark: Core is machine generated  :new: 

