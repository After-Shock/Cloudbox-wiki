## General Settings

1. Visit https://sonarr._yourdomain.com_ and click "Settings" -> "General", tick "Show Advanced Settings".
1. Set your branch to `develop`, like below.

    ![Sonarr Branch](http://i.imgur.com/JdQQlzS.png)

1. Set "Authentication" to `Forms`, then set a username and password.
1. Click "Save".



## Media Management

1. Click "Settings" -> "Media Management".
1. Enable "Rename Episodes".
1. Disable "Analyse video files".
1. Disable "Use hardlinks instead of copy".
1. Your settings should look similar to below.

    ![Sonarr settings - CloudBox](http://i.imgur.com/hURmo6Y.png)

1. Click "Save".



## Download Clients

1. Click "Settings" -> "Download Client".

1. Enable "Completed Download Handling" and "Remove" under it.

### NZBGet

1. Add a new "NZBGet" download client. 
1. Use `sonarr` as "Host", `6789` for "Port", and `sonarr` (lowercase) for "Category". Replacing the "Username" and "Password" with your own. Your settings will look like below.

    ![Sonarr NZBGet Downloader](http://i.imgur.com/EhOFFxK.png)

1. Click "Save" to add NZBGet.


### ruTorrent

1. Add a new "rTorrent" download client.
1. Use `sonarr` as "Host", `6789` for "Port", and `sonarr` (lowercase) for "Category". Replacing the "Username" and "Password" with your own. Your settings will look like below.
 
    ![Sonarr ruTorrent Downloader](http://i.imgur.com/kE701JT.png)

1. Click "Save" to add ruTorrent.



## Indexers

### NZB Hydra

1. Click "Settings" -> "Indexers".
1. Click Add Indexer (`+`).
1. Select "Newznab".  
1. For "Host", type in `nzbhydra:8080` for "Host".
1. For "API Key", paste in your NZB Hydra API Key (see [[NZB Hydra]]).
1. Your settings will look like this:
 
    ![Sonarr NZB Hydra](http://i.imgur.com/C05pVkA.png)

### Jackett

1. Click "Settings" -> "Indexers".

1. Click Add Indexer (`+`) 

1. Select "Torznab".  

1. For "Host", paste in the indexer's 'Torznab Feed" (see [[Jackett]]). Replace `https` with `http` and replace `jackett.yourdomain.com` with `jackett:8080`.

1. For "API Key", paste in your Jackett API Key (see [[Jackett]]).

1. Your settings will look like this: 

    ![Sonarr Jackett](http://i.imgur.com/DcmVyUC.png)

Note: These steps will need to done for each individual indexer you want to add. 




## Torrent Cleaner script

This custom script, will cleanup torrents from ruTorrent that were auto-extracted, but still being seeded. So if it detects that .rar files are in the folder that Sonarr just imported from, it will delete the imported video file(s), leaving just the .rar files for seeding.

1. Click "Settings" -> "Connect".
1. Add a new "Custom Script", and ensure the settings are the same as below. 

    ![Sonarr Torrent Cleanup Script CloudBox](http://i.imgur.com/nNkMLdB.png)


1. Click "Save" to add the script. 


## Plex Autoscan
Add info here

## Setting the TV Path
1. When you are ready to add your first show to Sonarr, click the "Path" drop-down and select "Add a different path". 

1. Click the blue "Browse" button, select `tv`, scroll to the bottom and select "OK".

1. Click the green "checkmark" button to add the path.
