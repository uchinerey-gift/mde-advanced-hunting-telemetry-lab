# STAR Interview Narrative — Microsoft Defender Telemetry Lab

## Situation
A lab environment was created to simulate real-world endpoint activity and validate that Microsoft Defender for Endpoint was correctly collecting file, process, and network telemetry.

## Task
Generate controlled security-relevant activity, confirm telemetry visibility in Advanced Hunting, and demonstrate the ability to investigate activity using KQL.

## Action
- Used PowerShell to create, modify, and delete files to generate `DeviceFileEvents`.
- Executed a controlled EICAR string to simulate suspicious process execution.
- Ran `Test-NetConnection` to produce `DeviceNetworkEvents`.
- Wrote KQL queries to correlate host, file, and network behaviors.
- Documented findings with screenshots and structured analysis.

## Result
- Verified full endpoint visibility across host, file, process, and network layers.
- Produced reusable KQL queries for incident investigation.
- Demonstrated practical SOC-style telemetry validation skills applicable to Tier-1/Tier-2 analyst workflows.
