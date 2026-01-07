# 🛡️ Microsoft Defender Advanced Hunting & PowerShell Telemetry Lab

![Status](https://img.shields.io/badge/Lab-In_Progress-yellow)
![Platform](https://img.shields.io/badge/Platform-Microsoft%20Defender-blue)
![Tools](https://img.shields.io/badge/Tools-KQL%20%7C%20PowerShell-orange)

## 🔹 Step 1 — Environment & Host Validation

Validated the lab environment by confirming the device name and user context.

**PowerShell Commands**
```powershell
hostname
whoami
```
---

**Screenshot — Environment Validation**
![Step 1 — Environment Validation](images/step1-environment-validation.png)


## 🔹 Step 2 — File Creation, Modification & Deletion Telemetry

Simulated normal and suspicious file activity to generate Microsoft Defender telemetry.

**PowerShell Commands**
```powershell
New-Item hi-today-1.txt
New-Item hi-today-2.txt
Remove-Item hi-today-1.txt
```

Screenshot — File Activity Executed in PowerShell  
![Step 2 — PowerShell File Activity](images/step2-file-activity-powershell.png)

Screenshot — File Events in Microsoft Defender (Advanced Hunting)  
![Step 2 — File Events in Defender Advanced Hunting](images/step2-file-events-advanced-hunting.png)

### Advanced Hunting Query — File Events

```kusto
DeviceFileEvents
| where DeviceName == "chi-chi-vm"
| where FileName startswith "hi-today"
| order by Timestamp desc
| take 50

