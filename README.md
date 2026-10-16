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
