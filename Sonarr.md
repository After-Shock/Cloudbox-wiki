1. Visit https://sonarr.domain.com and click Settings -> General, tick Show Advanced Settings.
2. Set your branch to develop, like below.
![Sonarr Branch](http://i.imgur.com/Ygmgwjj.png)
3. Set Authentication to Forms, then set a username and password.
4. Click Save Settings, then click Media Management.
5. Enable the renaming of episodes.
6. Untick anaalyse video files.
7. Untick use hardlinks instead of copy.
8. Your settings should look similar to below.
![Sonarr settings - CloudBox](http://i.imgur.com/kIHcg1q.png)
9. Click Save Settings, then click Download Client.
10. Enable remove on completed download handling.
11. Add a new nzbget downloader, ensure the settings are the same or similar as below, replacing the user/password with your own.
![Sonarr NZBGet Downloader](http://i.imgur.com/7CMeNL7.png)
12. Add a new rutorrent downloader, ensure the settings are the same or similar as below, replacing the user/password with your own.
![Sonarrr Rutorrent Downloader](http://i.imgur.com/TRVUMVB.png)
13. Click Save Settings, then click Connect.
14. Add a new Custom Script, and ensure the settings are the same as below.
![Sonarr Torrent Cleanup Script CloudBox](http://i.imgur.com/mLEaA4X.png)
This custom script, will cleanup torrents from rutorrent that were auto extracted. So if it detects that .rar files are in the folder that sonarr just imported from, delete the imported video file, leaving just the rar files for seeding.

add media:
sonarr is /tv



webhook
