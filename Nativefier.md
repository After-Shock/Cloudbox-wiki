[Nativefier](https://github.com/jiahaog/nativefier#nativefier) is a cross-platform application that allows you to turn any website into a self contained (Chrome-based) app. This way you can open your Cloudbox apps without having to deal with multiple tabs in your internet browser. You can use this as an alternative to [[Organizr]]. 


The following is a little guide to set Nativefier on the PC you want to access your server from (not on the server itself).


## 1. Setup Nativefier

Two ways to do this:

* Native Install

   1. Install [Node.js](https://nodejs.org/en/download/current)

   1. Install [Xcode](https://developer.apple.com/xcode) (only for macOS)

   1. Install [ImageMagick](https://www.imagemagick.org/script/download.php) (only for macOS)

   1. Install Nativefier via:

      ```
      npm install nativefier -g
      ```
* Download the docker [image](https://hub.docker.com/r/jiahaog/nativefier/) and use the [run command](https://github.com/jiahaog/nativefier#docker-image).

## 2. Create Nativefier Desktop Apps 

_Note: The below commands are for the native install._

### Basic Command


```
nativefier appname.domainname.com
```

### Some useful options. 

- Give it a name: `--name "App Name"`
- Disable dev tools: `--disable-dev-tools `
- Force a specific icon with `--icon "path/to/icon"`, where the path/to/icon can be a local file or online path.
- Force a zoom at start. Example `--zoom=0.8`. You can also change the zooms with `ctrl` + `+` and `ctrl` +  `-` (replace with `command` in macOS).
- To completely quit out of the app when you close the window (for macOS): `--fast-quit`

### Some examples you can use:

```
nativefier --name "Sonarr" "https://sonarr.domain.com"
nativefier --name "Radarr" "https://sonarr.domain.com"
nativefier --name "PlexPy" "https://plexpy.domain.com/home"
nativefier --name "Jackett" "https://jackett.domain.com/Admin/Dashboard"
nativefier --name "Plex Requests" "https://plexrequests.domain.com"
nativefier --name "NZBGet" "https://nzbget.domain.com"
nativefier --name "NZB Hydra" "https://nzbhydra.domain.com"
nativefier --name "ruTorrent" "https://rutorrent.domain.com"

```

## 3. Move the Nativefier App 

Copy the app (e.g.  `.app` in MacOS, `.exe` in Windows) to you preferred location (e.g. `Applications` in MacOS)





