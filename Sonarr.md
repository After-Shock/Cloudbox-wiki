## General Settings

1. Visit https://sonarr._yourdomain.com_ and click "Settings" -> "General", tick "Show Advanced Settings".
1. Set your branch to `develop`, like below.

    ![Sonarr Branch](http://i.imgur.com/JdQQlzS.png)

1. Set "Authentication" to `Forms`, then set a username and password.
1. Click "Save Settings".

## Media Management

1. Click "Settings" -> "Media Management".
1. Enable "Rename Episodes".
1. Disable "Analyse video files".
1. Untick use hardlinks instead of copy.
1. Your settings should look similar to below.

    ![Sonarr settings - CloudBox](http://i.imgur.com/kIHcg1q.png)
1. Click Save Settings, then click Download Client.
1. Enable remove on completed download handling.
1. Add a new nzbget downloader, ensure the settings are the same or similar as below, replacing the user/password with your own.
![Sonarr NZBGet Downloader](http://i.imgur.com/7CMeNL7.png)
1. Add a new rutorrent downloader, ensure the settings are the same or similar as below, replacing the user/password with your own.
![Sonarrr Rutorrent Downloader](http://i.imgur.com/TRVUMVB.png)
1. Click Save Settings, then click Connect.
1. Add a new Custom Script, and ensure the settings are the same as below.
![Sonarr Torrent Cleanup Script CloudBox](http://i.imgur.com/mLEaA4X.png)
This custom script, will cleanup torrents from rutorrent that were auto extracted. So if it detects that .rar files are in the folder that sonarr just imported from, delete the imported video file, leaving just the rar files for seeding.
1. Click Save Settings, then click Indexers.
1. To add NZBHydra, use similar settings to below, setting your api key. 
![Sonarr NZBHydra](http://i.imgur.com/H2gZmZn.png)
1. To add Jackett, use similar settings to below, obviously setting your api key, and your own indexer choices.
![Sonarr Jackett](http://i.imgur.com/3v9yAXj.png)

add media:
sonarr is /tv



webhook
