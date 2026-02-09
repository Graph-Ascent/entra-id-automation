# Security & Governance Framework

This document outlines the security principles applied to the scripts in this repository to ensure the protection of tenant data.

## 1. Principle of Least Privilege (PoLP)
Scripts are designed to function with the minimum required Graph API scopes. 
* **Read-only tasks** use `.Read.All` scopes.
* **Administrative tasks** are isolated to specific modules (e.g., `User.ReadWrite.All`) and never request `Directory.AccessAsUser.All` unless absolutely necessary.

## 2. Credential Management
* **Interactive Auth:** Recommended for manual runs. No credentials are stored locally.
* **Unattended Auth:** For automation, scripts support Certificate-Based Authentication (CBA). **Client Secrets are discouraged** in production environments.
* **Secrets Handling:** This repository uses `.gitignore` to prevent any local `.env` or configuration files from being committed to version control.

## 3. Data Sanitization
No Personal Identifiable Information (PII), Tenant IDs, or custom domain names are hardcoded. All scripts use variables or parameters:
* `$TenantId`
* `$DomainName`
* `$TargetUser`

## 4. Audit Trail
All actions performed by these scripts are logged in the **Entra ID Audit Logs** under the identity of the user or Service Principal executing the command.