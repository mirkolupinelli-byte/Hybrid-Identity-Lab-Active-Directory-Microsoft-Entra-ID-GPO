# Hybrid Identity Lab: Active Directory + Microsoft Entra ID + GPO

##  Overview

This project demonstrates the implementation of a hybrid identity environment by integrating an on-premises Active Directory (AD DS) with Microsoft Entra ID.

The lab simulates a real enterprise scenario where identity management is centralized and synchronized between on-prem infrastructure and the cloud. It includes user synchronization, group-based access control, Group Policy enforcement, and validation through a domain-joined client.

---

##  Architecture

The environment consists of:

* **Domain Controller (VM1)** hosting Active Directory Domain Services
* **Client Machine (VM2)** joined to the domain
* **Microsoft Entra ID tenant** for cloud identity
* **Entra Connect** for synchronization

### Key design elements:

* On-prem AD as the primary identity source
* Entra ID as the cloud identity platform
* Synchronization between AD and Entra
* Centralized policy enforcement via GPO

---

##  Components

* Active Directory Domain Services (AD DS)
* Microsoft Entra ID (Azure AD)
* Entra Connect (synchronization engine)
* Domain-joined client VM
* Group Policy Objects (GPO)
* File sharing with permissions
* Azure Virtual Network (VNet) infrastructure

---

##  Key Features

* Hybrid identity (AD → Entra ID synchronization)
* Domain join and authentication using AD credentials
* Group-based access control (RBAC-style logic)
* GPO enforcement (Control Panel restriction)
* Centralized identity management across environments
* Real-world troubleshooting of sync and connectivity issues

---

##  Implementation

### 1. Active Directory Setup

* Created domain: `mirko.local`
* Configured users and groups (e.g., IT group)
* Assigned permissions based on group membership

---

### 2. Entra ID Integration

* Configured Entra Connect
* Synchronized on-prem users to cloud tenant
* Validated user and group presence in Entra ID

---

### 3. Domain Join

* Created second VM (client)
* Configured DNS to point to Domain Controller
* Successfully joined domain (`mirko.local`)
* Logged in using domain credentials

---

### 4. Group Policy (GPO)

* Created GPO to restrict Control Panel access
* Linked GPO to domain
* Forced update using `gpupdate /force`
* Verified policy enforcement on client VM

---

### 5. File Sharing

* Created shared folder on Domain Controller
* Assigned access using AD group (IT)
* Verified access from domain-joined client

---

##  Troubleshooting & Lessons Learned

This lab included several real-world issues that were identified and resolved:

* **Entra Connect authentication error**

  * Cause: incorrect tenant/user mismatch
  * Fix: used internal tenant user instead of external (#EXT#)

* **Domain join failure**

  * Cause: incorrect DNS configuration
  * Fix: configured VM DNS to point to Domain Controller

* **RDP login issues**

  * Cause: confusion between local and domain users
  * Fix: used proper login formats (`.\user`, `domain\user`)

* **GPO wallpaper issue**

  * Policy applied correctly but not visible due to RDP session limitations
  * Verified functionality through policy application and file access

---

##  Screenshots

* Domain join success
* GPO configuration
* Control Panel blocked (policy working)
* Entra ID sync success
* Initial sync error (before fix)

---

##  Outcome

Successfully deployed a hybrid identity environment integrating on-prem Active Directory with Microsoft Entra ID.

The system supports synchronized users, centralized access control via groups, enforced policies via GPO, and validated authentication from a domain-joined client machine.

---

##  Skills Demonstrated

* Identity & Access Management (IAM)
* Active Directory administration
* Microsoft Entra ID integration
* Hybrid infrastructure design
* Group Policy management
* Networking fundamentals (DNS, domain join)
* Troubleshooting real-world issues

---

##  Notes

This project focuses on practical implementation and troubleshooting rather than theoretical configuration. It reflects real-world challenges encountered in enterprise environments.

---
