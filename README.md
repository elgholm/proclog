# proclog

Script to collect various process information about what's running on the system at the called moment.  
Information is saved under the /tmp/proclog directory, e.g. /tmp/proclog/2023-04-14/185652.txt

```
Usage:
    ./proclog 2 3 email@address.net
    2 = Only run if 1-min load average is greater than or equal to 2.
    3 = Run 3 iterations (default 5).
    email@address.net = Send email to email@address.net (default "" = no email)
```

Please see the script for more information and all settings.

Note: This script uses iotop, so that must be installed.

PS. Yes, I know about sa, pminfo/pmrep, auditd, etc. But they don't show me what I want to see,  
    or I just don't understand them well enough. This I understand.

Tip: When running from cron, set the environment variable RUN_BY_CRON to some value.
cron Example:
```
* * * * * export RUN_BY_CRON=Y; /root/scripts/proclog 3 3 email@address.net
```

Cheers!
/Charlie Elgholm 2023-04-14
