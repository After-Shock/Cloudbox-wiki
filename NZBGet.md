## 1. Accessing NZBGet

1. To access NZBGet, visit https://nzbget._yourdomain.com_

## 2. Setup

1. Go to "Settings" -> "Security". 
    1. Set a "ControlUsername" and "ControlPassword", then set an "AddUsername" and "AddPassword" to protect API access. 

    1. Select "Form Auth", then click "Save" and "Reload".
1. Add your news servers.
1. Download paths have already been specified, no need to change those.
1. If you want to use scripts, place them in `/opt/scripts/nzb` on your server, as this is where NZBGet will load scripts from.