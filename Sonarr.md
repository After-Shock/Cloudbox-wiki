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

## Connect

### Torrent Cleaner script

This custom script, will cleanup torrents from ruTorrent that were auto-extracted, but still being seeded. So if it detects that .rar files are in the folder that Sonarr just imported from, it will delete the imported video file(s), leaving just the .rar files for seeding.

1. Click "Settings" -> "Connect".
1. Add a new "Custom Script", and ensure the settings are the same as below. 

    ![Sonarr Torrent Cleanup Script CloudBox](http://i.imgur.com/mLEaA4X.png)


1. Click Save Settings, then click Indexers.
1. To add NZBHydra, use similar settings to below, setting your api key. 
![Sonarr NZBHydra](http://i.imgur.com/H2gZmZn.png)
1. To add Jackett, use similar settings to below, obviously setting your api key, and your own indexer choices.
![Sonarr Jackett](http://i.imgur.com/3v9yAXj.png)

add media:
sonarr is /tv



webhook
