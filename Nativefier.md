[Nativefier](https://github.com/jiahaog/nativefier) is a cross-platform application that allows you to turn any website into a self contained (Chrome-based) app. Below I present a little guide on how you can use this as an alternative to Organizr. 

## 1. Install Nativefier

You could run this via docker, but I haven't tested that myself. 

1. Install [Node.js](https://nodejs.org/en/download/current)

1. Install [ImageMagick](https://www.imagemagick.org/script/download.php)

1. Install [Xcode](https://developer.apple.com/xcode) (only for MacOS)

1. Install Nativefier via:

   ```
   npm install nativefier -g
   ```

## 2. Create Nativefier Desktop Apps

Basic Command:
```
nativefier --fast-quit --disable-dev-tools  --name "App Name" "https://appname.domainname.com" /path/where/app/is/saved/
```

You can also force it to use a specific icon with `--icon "path"`

## 3. Move the Nativefier app 

Copy the app (e.g  `.app` in MacOS, `.exe` in Windows) to you preferred location (e.g. `Applications` in MacOS)


## 4.  Some examples below

```
nativefier --fast-quit --disable-dev-tools --name "Sonarr" "https://sonarr.domain.com" ~/nativefier
nativefier --fast-quit --disable-dev-tools --name "Radarr" "https://sonarr.domain.com" ~/nativefier
nativefier --fast-quit --disable-dev-tools --name "PlexPy" "https://plexpy.domain.com/home" --icon "https://raw.githubusercontent.com/JonnyWong16/plexpy/master/data/interfaces/default/images/res/android/icon-512x512.png" ~/nativefier 
nativefier --fast-quit --disable-dev-tools --name "Jackett" "https://jackett.domain.com/Admin/Dashboard" --icon "https://raw.githubusercontent.com/Jackett/Jackett/master/src/Jackett/Content/jacket_medium.png" ~/nativefier 
nativefier --fast-quit --disable-dev-tools --name "Plex Requests" "https://plexrequests.domain.com" ~/nativefier
nativefier --fast-quit --disable-dev-tools --name "NZBGet" "https://nzbget.domain.com/" --icon "https://avatars3.githubusercontent.com/u/3368377?v=3&s=400" ~/nativefier
nativefier --fast-quit --disable-dev-tools --name "NZB Hydra" "https://nzbhydra.domain.com" ~/nativefier
nativefier --fast-quit --disable-dev-tools --name "ruTorrent" "https://rutorrent.domain.com" ~/nativefier

```


