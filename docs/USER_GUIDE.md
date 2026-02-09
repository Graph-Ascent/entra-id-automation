# Entra ID Automation User Guide

This guide provides instructions on how to use the automation scripts in this repository to manage and audit your Entra ID environment.

## Table of Contents
1. [Prerequisites](#prerequisites)
2. [Authentication](#authentication)
3. [Running Audit Reports](#running-audit-reports)
4. [User Management Tasks](#user-management-tasks)

## Prerequisites
Before running any scripts, ensure the following are installed:
* **PowerShell 7.x** (Preferred for performance)
* **Microsoft Graph PowerShell SDK**:
  ```powershell
  Install-Module Microsoft.Graph -Scope CurrentUser