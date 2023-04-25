proclog

Script to collect various process information about what's running on the system at the called moment.  
Information is saved under the /var/log/proclog directory, e.g. /var/log/proclog/2023-04-25/121314.txt  
Version 1.1

Usage:
```
        ./proclog 2 3 email@address.net [daemon]
        2 = Only run if 1-min load average is greater than or equal to 2.
        3 = Run 3 iterations (default 3).
        email@address.net = Send email to email@address.net (default "" = no email)
        daemon = run as a daemon (exits when /var/log/proclog/dpid is removed)

        Please see the script for more information and all settings.
```

Please see the script for more information and all settings.

Note: This script uses iotop, so that must be installed.

PS. Yes, I know about sa, pminfo/pmrep, auditd, etc. But they don't show me what I want to see,  
    or I just don't understand them well enough. This I understand.

Run this from systemd using this service file:
```
[Unit]
Description=proclog daemon

[Service]
ExecStart=/root/scripts/proclog 2 3 email@address.net yes
ExecStop=/usr/bin/rm -f /var/log/proclog/dpid
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

When running from cron, set the environment variable RUN_BY_CRON to some value:
```
* * * * * export RUN_BY_CRON=Y; /root/scripts/proclog 3 3 email@address.net
```

Cheers!  
/Charlie Elgholm 2023-04-25
