# Windows Firewall Configuration Task

## Objective
As part of a cybersecurity internship task, the goal was to configure Windows Firewall rules using PowerShell to:

1. **Block Telnet (Port 23)** – Deny inbound connections.
2. **Allow SSH (Port 22)** – Permit inbound connections.

---

## Steps Performed

### Step 1: List Existing Firewall Rules
```powershell
Get-NetFirewallRule
```
- This command lists all existing firewall rules in the system.
- Verified that no rule with the name "Internship Block Telnet" existed.

### Step 2: Create "Block Telnet" Rule
```powershell
New-NetFirewallRule -DisplayName "Block Telnet" -Direction Inbound -LocalPort 23 -Protocol TCP -Action Block
```
- Successfully created a firewall rule to block Telnet (port 23).
- Rule was parsed and saved in the local persistent store.

### Step 3: Verify Telnet Block
```powershell
Test-NetConnection -ComputerName localhost -Port 23
```
- Attempted to connect to port 23 on localhost.
- Output:
  ```
  TcpTestSucceeded : False
  ```
- Indicates Telnet is successfully blocked by the rule.

### Step 4: Create "Allow SSH" Rule
```powershell
New-NetFirewallRule -DisplayName "Allow SSH" -Direction Inbound -LocalPort 22 -Protocol TCP -Action Allow
```
- Successfully added a rule to allow SSH connections on port 22.

---

## Final Verification

### Check Rules with Matching Display Names
```powershell
Get-NetFirewallRule | Where-Object DisplayName -like "*Telnet*"
Get-NetFirewallRule | Where-Object DisplayName -like "*SSH*"
```
- Confirmed both rules were added correctly.

---

## Screenshots
Screenshots demonstrating the execution of the above steps have been included in the attached Word document:
- 📄 `Firewall_Task_Report_Naveen_Kumar.docx`

---

## Author
**Naveen Kumar**  
Cybersecurity Internship Task – Firewall Rules Configuration  
Date: May 30, 2025
