NZBGet is a very efficient, cross-platform usenet downloader.

## 1. Accessing NZBGet

- To access NZBGet, visit https://nzbget._yourdomain.com_

## 2. Setup

1. Go to "Settings" -> "Security".
 
    1. Set a "ControlUsername" and "ControlPassword".

    1. Set an "AddUsername" and "AddPassword" to protect API access. 

    1. Select "Form Auth" to `Yes`

    1. Click "Save" and then "Reload".

1. Add your [[news servers| Basics: Prerequisites#i-usenet]].

1. Download paths have already been specified, no need to change those.

## 3. Addons

If you want to use scripts, place them in `/opt/scripts/nzb` on your server. This will be accessed from within NZBGet via `/scripts`. 