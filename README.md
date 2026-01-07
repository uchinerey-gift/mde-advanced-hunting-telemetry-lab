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


### Advanced Hunting Query — File Events

```kusto
DeviceFileEvents
| where DeviceName == "chi-chi-vm"
| where FileName startswith "hi-today"
| order by Timestamp desc
| take 50
```

Screenshot — File Events in Microsoft Defender (Advanced Hunting)  
![Step 2 — File Events in Defender Advanced Hunting](images/step2-file-events-advanced-hunting.png)

## 🔹 Step 3 — Suspicious Process Execution Telemetry

Generated endpoint telemetry by simulating suspicious command activity in PowerShell.

**PowerShell Command**
```powershell
cd $env:USERPROFILE/Desktop
echo 'X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*' >> big-malware-today.exe
```

Screenshot — Process Execution in PowerShell  
![Step 3 — PowerShell Process Execution](images/step3-process-execution-powershell.png)


### Advanced Hunting Query — Process Events

```kusto
DeviceFileEvents
| where DeviceName == "chi-chi-vm"
| where FileName contains "big-malware"
| project Timestamp, DeviceName, ActionType, FileName, FolderPath, InitiatingProcessFileName
| order by Timestamp desc
| take 50
```

Screenshot — Process Events in Microsoft Defender (Advanced Hunting)  
![Step 3 — Process Events in Defender Advanced Hunting](images/step3-process-events-advanced-hunting.png)

## 🔹 Step 4 — Network Connection Telemetry

Simulated outbound network connections to generate Microsoft Defender telemetry for host-level network activity.

**PowerShell Commands**
```powershell
Test-NetConnection -ComputerName 8.8.8.8 -Port 443
Test-NetConnection -ComputerName 1.1.1.1 -Port 443
Test-NetConnection -ComputerName 8.8.8.8 -Port 53
hostname
```



