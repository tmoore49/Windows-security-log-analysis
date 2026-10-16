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
