# Object
- An object can be defined as ANY resource present within an Active Directory environment such as OUs, printers, users, domain controllers, etc.

# Attributes
- Every object in Active Directory has an associated set of attributes used to define characteristics of the given object
- A computer object contains attributes such as the hostname and DNS name
- All attributes in AD have an associated LDAP name that can be used when performing LDAP queries, such as displayName for Full Name and given name for First Name

# Schema
- The active directory schema is essentially the blueprint of any enterprise environment
- It defines what types of objects can exist in the AD database and their associated attributes
- It lists definitions corresponding to AD object and holds information about each object

# Domain
- A domain is a logical group of objects such as computers, users, OUs, groups, etc.
- We can think of each domain as a different city within a state or country
- Domains can operate entirely independently of one another or be connected via trust relationships

# Forest
- A forest is a collection of Active Directory domains
- It is the topmost container and contains all of the AD objects
- A forest can contain one or multiple domains and be thought of as a state in the US
- Each forest operates independently but may have various trust relationships with other forests

# Tree
- A tree is a collection of Active Directory domains that beings at a single root domain
- A forest is a collection of AD tress
- Each domain in a tree shares a boundary with the other domains
- A parent-child trust relationship is formed when a domain is added under another domain in a tree
- Two trees in the same forest cannot share a name

# Container
- Container objects hold other objects and have a defined place in the directory sub tree hierarchy

# Leaf
- Leaf objects do not contain other objects and are found at the end of the sub tree hierarchy

# Global Unique Identifier (GUID)
- A GUID is a unique 128-bit value assigned when a domain user or group is created
- This GUID value is unique across the enterprise, similar to a MAC address
- Every single object created by AD is assigned a GUID, not only user and group objects
- The GUID is stored in the ObjectGUID attribute
- When querying for an AD object, we can query for its objectGUID value using PowerShell or search for it by specifying its distinguished name. GUID, SID, or SAM account name
- GUIDs are used by AD to identify objects internally 

# Security Principals
- Security principals are anything that the operating system can authenticate, including users, computer accounts, or even threads/processes that run in the context of a user or computer account
- In AD, security principles are domain object that can manage access to other resources within the domain
- We can also have local user accounts and security groups used to control access to resources on only that specific computer

# Security Identifier (SID)
- A security identifier, or SID is used a unique identifier for a security principal or security group
- Every account, group, or process has its own unique SID, which, in an AD environment, is issued by the domain controller and stored in a secure database
- Even if the security principle is deleted, it can never be used again in that environment to identify another user or group

# Distinguished Name (DN)
- A DN describes the full path to an object in AD

# Relative Distinguished Name (RDN)
- A RDN is a single component of the Distinguished Name that identifies the object as unique from other objects at the current level in the naming hierarchy
- AD does not allow two objects with the name name under the same parent container, but there can be two objects with the RDNs that are still unique in the domain because they have different DNs

# sAMAccountName
- The sAMAccountName is the user's logon name

# userPrincipalName
- The userPrincipalName attribute is another way to identify users in AD
- This attribute consists of a prefix and a suffix

# FSMO Roles
- FSMO roles give the Domain Controllers (DC) the ability to continue authenticating users and granting permissions without interruption
- There are five FSMO roles: Schema Master and Domain Naming Master, Relative ID (RID) Master, Primary Domain Controller (PDC) Emulator, and Infrastructure Master
- All five roles are assigned to the first DC in the forest root domain in a new AD forest
- Each time a new domain is added to a forest, on the RID Master, PDC Emulator, and Infrastructure Master roles are assigned to the new domain

# Global Catalog (GC)
- A GC is a domain controller that stores copies of ALL objects in an Active Directory forest
- The GC stores a full copy of all objects in the current domain and a partial copy of objects that belong to other domain in the forest
- The GC allows both users and applications to find information about any objects in ANY domain in the forest

# Read-Only Domain Controller (RODC)
- A Read-Only Domain Controller (RODC) has a read-only Active Directory database
- No AD account passwords are cached on an RODC
- No changes are pushed out via an RODC's AD database, SYSVOL, or DNS 
- RODCs also include a read-only DNS server, allow for administrator role separation, reduce replication traffic in the environment, and prevent SYSVOL modifications from being replicated to other DCs

# Replication
- Replication happens in AD when AD objects are updated and transferred from one Domain Controller to another
- Whenever a DC is added, connection objects are created to manage replication between them
- These connections are made by the Knowledge Consistency Checker (KCC) service, which is present on all DCs
- Replication ensures that changes are synchronized with all other DCs in a forest, helping to create a backup in case one domain controller fails

# Service Principle Name (SPN)
- A SPN uniquely identifies a service instance
- They are used by Kerberos authentication to associate an instance of a service with a logon account, allowing a client application to request the service to authenticate an account without needing to know the account name

# Group Policy Object (GPO)
- GPOs are virtual collections of policy settings
- Each GPO has a unique GUID
- A GPO can contain local file system settings or Active Directory settings
- GPO settings can be applied to both user and computer objects
- They can be applied to both user and computer objects

# Access Control Lists (ACLs)
- An ACL is the ordered collection of Access Control Entities that apply to an object

# Access Control Entries (ACEs)
- Each ACE in an ACL identifies a trustee and lists the access rights that are allowed, denied, or audited for the given trustee

# Discetionary Access Control Lists (DACL)
- DACLs define which security principles are granted or deined access to an object; it contains a list of ACEs
- When a process tries to access a securable object, the system checks the ACEs in the object's DACL to determine whether or not to grant access
- If an object does NOT have a DACL
