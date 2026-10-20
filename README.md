# Active Directory Domain Services Lab
## Overview
This project documents the deployment and administration of an on-premises-style Active Directory Domain Services environment hosted in Microsoft Azure.
The lab includes a domain controller, a domain-joined client, centralized user management, account security policies, and Group Policy enforcement.

## Technologies Used
- Microsoft Azure
- Windows Server 2022
- Active Directory Domain Services
- DNS
- Group Policy
- Remote Desktop Protocol

## Implementation
1. Created an isolated Azure resource group and virtual network.
2. Deployed DC-1 and Client-1 in the same subnet.
3. Assigned DC-1 a static private IP.
4. Restricted RDP access to the administrator’s public IP.
5. Installed Active Directory Domain Services and DNS.
6. Created the corp.example.test forest and domain.
7. Configured Client-1 to use DC-1 for DNS.
8. Joined Client-1 to the domain.
9. Created _ADMINS, _CLIENTS, and _EMPLOYEES organizational units.
10. Created a dedicated domain-administrator account.
11. Used PowerShell to create six fictional employee accounts.
12. Configured account lockout protection.
13. Practiced disabling, enabling, and resetting an employee account.
14. Created and applied a client inactivity-lock Group Policy.

## Active Directory Structure
The directory separates administrators, employee accounts, and managed client computers into organizational units.
<img width="617" height="420" alt="image" src="https://github.com/user-attachments/assets/9f202156-7c3a-484c-81db-e8c0f1886f4f" />

## Account Lockout Policy
The domain was configured to lock an account after five invalid sign-in attempts. The lockout duration and counter-reset period are both 15 minutes.
<img width="546" height="79" alt="image" src="https://github.com/user-attachments/assets/d157901c-5d3e-4943-8ecd-f54b57bb7939" />

## Client Security Policy
A Group Policy Object linked to the _CLIENTS OU locks inactive computers after 900 seconds.
<img width="568" height="63" alt="image" src="https://github.com/user-attachments/assets/b270e462-49ca-44c4-8cdb-f67b48bc7edf" />

## Policy Verification
`gpresult` confirmed that the Default Domain Policy and Client Security Policy were applied to Client-1. The registry value confirmed the 900-second inactivity timeout.

<img width="601" height="182" alt="image" src="https://github.com/user-attachments/assets/3d2e60d6-93c6-4df5-9cba-5465c794b227" />

## Security and Cost Controls
- RDP was restricted using Azure Network Security Group rules.
- Public IP addresses and credentials were excluded from this repository.
- The domain controller uses a static private IP.
- Administrative and standard employee accounts were kept separate.
- Both Azure VMs were stopped and deallocated after the lab.

## Skills Demonstrated
- Deploying Active Directory Domain Services
- Configuring AD-integrated DNS
- Joining a computer to a domain
- Managing users, computers, and organizational units
- Creating and applying Group Policy
- Managing disabled accounts and password resets
- Applying least-privilege and cost-control practices
