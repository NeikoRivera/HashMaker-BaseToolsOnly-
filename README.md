# HashMaker-BaseToolsOnly-

This tool set will only use internal Windows,Linux, and Unix Tools to create Hashes of files.
Another file will also contain MD5,SHA128,SHA256 baselines of all clean installed systems by 
year if we decide to go more in depth then we will do by update. With these files you will 
be able to RUN a DIF command to see what has changed.

### Prerequisites

Knowledge of:<br />
Powershell <br />
CMD (maybe..) <br />
Bash <br />
<br />
### Use
<br />
This tool can be used to see comparisons in updates or in Incident Response Techniques.
One example is you install an update and something breaks. By comparing MD5 hashes you
can see if a file has been changed or if a file was added or removed. 
<br />
For incident Response if we take a baseline of a system and something happens we can check
the most recent files and then by running this we can run a dif on the file and compare 
what has changed.
<br />
### Problems
Many False Positives
depending on file size or directory size it may take a while to create all hashes<br />
Hidden Files on systems also need hashes<br />
Will this work on a file with no privs<br />
What if the file is chattr'd<br />
If file is used by another process<br />

### Possible Solutions
Find a way to add exceptions for dirs<br />
None yet<br />
Add a parameter for this (Doesn't take long)<br />
NO - Need a way to create hash anyways<br />
It might still work it depends on the situation<br /><br />
I havent figured this out yet<br /><br />
<br />
### Example
<br />
PowerShell Output<br />

'''
Algorithm       Hash                                                                   Path <br />
---------       ----                                                                   ----
MD5             55F49769891E4DC7CAB3E293E1238888                                       C:\Windows\bfsvc.exe<br />
MD5             289C7B8CF6D1DEBD2CA0D050B6245FC5                                       C:\Windows\appcompat\UA\Appra...<br />
MD5             7EC4F8DC8EE3B2F23BD56EB3891C4C09                                       C:\Windows\appcompat\UA\Gener...<br />
MD5             0674C977436D5BA069F3CEBA57438469                                       C:\Windows\apppatch\AcRes.dll<br />
MD5             B86E24B9EA45AAB2E7EA40B47E9985C7                                       C:\Windows\apppatch\drvmain.sdb<br />
MD5             31CC816ECE45AD2A3966079296C08547                                       C:\Windows\apppatch\frxmain.sdb<br />
MD5             BE1799B1553F8113135D2C4AAA115BBF                                       C:\Windows\apppatch\msimain.sdb<br />
MD5             EECA90877F9B95771BC9957E5D4A74CB                                       C:\Windows\apppatch\pcamain.sdb<br />
MD5             7463A998F3EE774A2A5EC6DBDA14AB5D                                       C:\Windows\apppatch\sysmain.sdb<br />
MD5             121F34E1169133555592402766270712                                       C:\Windows\apppatch\en-US\AcR...<br />
'''
###Issue
'''<br />
get-filehash : The file C:\Windows\bootstat.dat cannot be read: The process cannot access the file<br />
C:\Windows\bootstat.dat because it is being used by another process.<br />
At line:1 char:27<br />
dir c:\Windows -Recurse | get-filehash -Algorithm MD5<br />
  CategoryInfo          : ReadError: (C:\Windows\bootstat.dat:PSObject) Write-Error, WriteErrorException<br />
  FullyQualifiedErrorId : FileReadError,Get-FileHash<br />
'''<br />

### License<br />
The GNU GPLv3 is a copyleft license that requires anyone who distributes your code
or a derivative work to make the source available under the same terms, and also 
provides an express grant of patent rights from contributors to users.
