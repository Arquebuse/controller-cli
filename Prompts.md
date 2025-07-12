# Prompts used for project creation and implementation

## Blueprint creation (ChatGPT o4-mini-high + Deep reaserch)

You are a senior Windows architect and .NET developer. 

You work on the Arquebuse project: An open‑source notification system delivering secure, targeted Windows alerts with enterprise‑focused simplicity. This project is based on 3 distinct modules:
- **Desktop‑App**: Windows service that registers with WNS, receives and displays notifications.
- **Controller‑Core**: .NET 8 Minimal API managing client registrations, AD queries, and sending WNS notifications (uses SQLite).
- **Controller‑CLI**: PowerShell Core module to manage subscriptions and send notifications via Controller‑Core.

I need an MVP blueprint for the **Arquebuse Controller-CLI** module that:

- Runs cross-platform on PowerShell 7+  
- Connects over HTTPS to the Controller-Core API (handling self-signed certs)  
- Provides cmdlets to:
  1. List subscribers (`Get-ArquebuseSubscribers` with AD filters)  
  2. Send notifications (`Send-ArquebuseNotification` with AD filters and message)

Please produce, in concise bullet points:

1. **High-Level Architecture Diagram** showing:
   - How the CLI authenticates to Controller-Core  
   - How cmdlets parse AD filters and format REST calls  
   - Where logs or responses are displayed  
2. **Folder/module structure** for a PowerShell module (psd1, psm1, README).
3. **Key function sketches** (pseudo-code) for each cmdlet:
   - Parameter definitions (filter objects, message string)  
   - REST invocation using `Invoke-RestMethod`  
   - TLS/certificate handling logic  
   - Output formatting  
4. **Sample configuration snippets**:
   - Module manifest (psd1)  
   - Example PowerShell profile snippet to trust the dev certificate  
5. **Step-by-step setup instructions** for a beginner:
   - How to install the module locally  
   - How to configure `$Env:Arquebuse_ApiUrl` and certificate trust  
   - Example calls to list subscribers and send a notification  
6. **Best practices** references:
   - Secure storage of API credentials or tokens  
   - PowerShell error handling and logging  
7. Explain exactly **how this Controller-CLI will integrate** with:
   - The **Controller-Core** (endpoints consumed)  
   - The **Desktop-App** (expected client registration records)

Use the readme.md in the arquebuse/desktop-app github repository to get more information about this module.

Finally, if any details on REST schemas, AD filter formats, or PowerShell packaging are unclear, ask me for more info.
