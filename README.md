# Windows-security-log-analysis
Windows security log analysis investigation failed logins and suspicious activity.
## MSSQL Failed Logon Investigation

### Objective
I investigated a series of failed logon events (Event ID 18456) on an MSSQL server to identify the source IP attempting to gain unauthorized access, determine the type of attack and confirm whether the attack was successful.

### Environment and setup
- Acer Chromebook running Linux
- Python3-evtx(evtx_dump.py) to decode Windows event logs
- EVTX-ATTACK-SAMPLES repository from Github
- Log file: MSSQL_multiple_Failed_logon_EventID_18456.evtx

### Evidence 
<img width="1920" height="1080" alt="zero 1 setup" src="https://github.com/user-attachments/assets/33977dec-925d-40f4-aaa5-5cc069c3d313" />
*Setup: Installing Python3-evtx and locating the MSSQL Log file*

<img width="1920" height="1080" alt="02 -investigation" src="https://github.com/user-attachments/assets/62f1a5b2-084b-444f-8170-34a9ea134291" />
*Investigation: Decoded events showing failed logon from 10.0.2.17 against the sa account*

### Findings
- Source IP 10.0.2.17
- 10 failed logons(Event ID 18456),0 successful logons(Event ID 18454)
- All attempts within the same second (13:46:01,Nov 4 2019) too fast for a human indicating that this was an automated tool
- Target: MSEDGEWIN10(MSSQL server),account "sa"(built in SQL Server admin), reason Password did not match
- Attacker also tried a windows (NT) account name through SQL Server authentication,a second login method
- outcome no successful logons,so the attack failed

### MITRE ATT&CK Mapping
- Tactic:Credential Access
- Technique: Brute force (T1110)

 ### Lessons Learned
- How to decode and investigate Windows event logs from an MSSQL server on Linux
- Timestamps can reveal whether an attack is automated or human: 10 attempts in one second point to a tool
- Timestamps build the attack timeline and let you correlate events across other logs and systems.
- Log timestamps are usually in UTC,so you have to convert it to match other resources.

  ### Recommendations
- Disable or rename the built-in "sa" account
- Enable account lockout after repeated failed logons
- block or investigate source IP 10.0.2.17
- Create SIEM alert for multiple 18456 events from one IP in a short time
- Restrict MSSQL access so the server isn't reachable from untrusted network 
