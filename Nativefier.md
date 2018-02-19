[Nativefier](https://github.com/jiahaog/nativefier#nativefier) is a cross-platform, Electron application (built on Chromium and Node.js), that allows you to turn any website into a native OS app. This way you can easily "open" and "close" your Cloudbox apps without having to use a bulky internet browser, meaning you won't need to hunt down the tab where you had something open, anymore, and less memory usage.  You can easily use this to replace [[Organizr | First-Time-Install: Organizr]]. 




Screenshots (macOS):

![](https://i.imgur.com/bHYzgix.png)


![](https://i.imgur.com/QnTjO7e.png)




The following steps will guide you through setting up Nativefier on your PC:


## 1. Setup Nativefier


   1. Install [Node.js](https://nodejs.org/en/download/current)

   1. For macOS, install [Xcode](https://developer.apple.com/xcode) and [ImageMagick](https://www.imagemagick.org/script/download.php) <a href="#note1" id="note1ref"><sup>[1]</sup></a>

      - _Note: This is only needed for automatic website icon to app icon conversion. If you want to skip installing Xcode and ImageMagick, but still want to be able to customize the application icon, you can do so by; first, finding a transparent png of the application (e.g. google image search `transparent png <appname>), and then, following directions on this <a href="https://support.apple.com/en-us/HT201737">page</a>_.

   1. Install Nativefier with this command:

      ```
      sudo npm install nativefier -g
      ```

## 2. Create Nativefier Desktop Apps 
![](https://github.com/jiahaog/nativefier/raw/master/screenshots/walkthrough.gif)

### Basic Command




```
nativefier appname.domainname.com
```




### Some Useful Options

- Give it a name: `--name "App Name"`
- Add Basic HTTP Authentication: `--basic-auth-username <yourusername> --basic-auth-password <yourpassword>`
  - Note: If you plan to use this, set your apps to use HTTP Authentication as well (e.g. Sonarr, Radarr, NZBGet, NZB Hydra, and PlexPy).
- Disable dev tools: `--disable-dev-tools`
- Force a specific icon with `--icon "path/to/icon"`, where the path/to/icon can be a local file or online path.
- Force a zoom at start: Example `--zoom=<zoomlevel>` (example: `--zoom=0.8`). 
  - You can also change the zooms with `ctrl` + `+` and `ctrl` +  `-` (replace with `command` in macOS).
- In macOS, to completely quit out of the app when you close the window: `--fast-quit`

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

### Example for MacOS (after enabling HTTP authentication)


```
nativefier --name "Sonarr" --basic-auth-username myusername --basic-auth-password mypassword --fast-quit --disable-dev-tools "https://sonarr.domain.com"
```



## 3. Move the Nativefier App 

Copy the app (e.g.  `.app` in MacOS, `.exe` in Windows) to your desktop or the applications location (i.e. Applications folder in MacOS, Start Menu in Windows)

