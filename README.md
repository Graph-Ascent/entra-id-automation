# Entra ID & Microsoft 365 Identity Automation

![Entra ID](https://img.shields.io/badge/Microsoft-Entra%20ID-blue?style=for-the-badge&logo=microsoft-azure)
![PowerShell](https://img.shields.io/badge/PowerShell-5.1%20%2F%207%2B-blue?style=for-the-badge&logo=powershell)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

A specialized collection of **Microsoft Graph SDK** scripts designed to automate user lifecycle management, security auditing, and tenant governance. These tools are built for scale, prioritizing **Least Privilege** and **Zero Trust** principles.

## Key Solutions

| Script | Function | Business Value |
| :--- | :--- | :--- |
| `Get-InactiveUserReport.ps1` | Identifies users inactive for 30+ days. | **Cost Optimization:** Reclaim unused licenses. |
| `Invoke-BulkUserCreation.ps1` | Automates onboarding via CSV with secure pass generation. | **Efficiency:** Reduces onboarding time by 90%. |
| `Get-MFAReport.ps1` | Audits MFA status for all tenant users. | **Security:** Identifies gaps in identity protection. |
| `New-GraphAppRegistration.ps1` | Configures secure Service Principals for automation. | **Governance:** Replaces risky global admin accounts. |

---

## Getting Started

### Prerequisites
* **PowerShell 7+** (Recommended) or PowerShell 5.1.
* **Microsoft Graph SDK** modules. Install via:
  ```powershell
  Install-Module Microsoft.Graph.Users, Microsoft.Graph.Authentication -Scope CurrentUser

graph TD
    %% Define Nodes
    HR[Authoritative Source<br/>'HR / CSV / SQL'] -- "New Hire Signal" --> Script[<b>Your PowerShell Engine</b><br/>'Microsoft Graph SDK']
    
    %% Lifecycle Actions
    subgraph "Identity Lifecycle Management"
    Script -- "Day 1" --> Provision[Provision Entra ID Account]
    Provision --> License[Assign M365 Licenses]
    License --> Security[Apply Zero-Trust CA Policies]
    end
    
    %% Continuous Governance
    subgraph "Ongoing Governance"
    Audit[Audit: Inactive Users] -- "Alert" --> Script
    MFA[Audit: MFA Gaps] -- "Report" --> Admin[Admin Dashboard]
    end
    
    %% Offboarding
    Term[Termination Signal] -- "Instant Trigger" --> Offboard[Automated Offboarding]
    Offboard --> Revoke[Revoke Tokens & Disable]
    Revoke --> Archive[Archive Data / Reclaim License]

    %% Styling
    style Script fill:#0078d4,color:#fff,stroke:#005a9e
    style HR fill:#f3f2f1,stroke:#323130
    style Offboard fill:#d83b01,color:#fff
