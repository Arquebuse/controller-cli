# Arquebuse controller CLI

PowerShell module for administrators to interact with the Controller‑Core service: managing subscriptions and sending targeted notifications.

## Goals

- Simplify subscription management via scripts
- Send alerts without direct HTTP coding

## Architecture

- PowerShell module exposing functions that wrap REST API calls
- Configurable base URI and certificate trust settings

## Technologies

- PowerShell 7+, `Invoke-RestMethod`, TLS

## Example Usage

```powershell
Import-Module ArquebusePS

# List subscribers in group 'HR'
Get-Subscribers -Filter @{Group='HR'}

# Send outage alert to group 'IT'
Send-Notification -Filter @{Group='IT'} -Message 'Critical service outage ongoing'
```

## Backlog

-  Cross-platform compatible (PowerShell Core)
-  Connect securely to Controller-Core via HTTPS (optionally accepting self-signed certs during development)
-  Command to retrieve list of subscribed users/computers from Controller-Core
-  Command to create/send targeted notifications based on AD filters (users, groups, computers)