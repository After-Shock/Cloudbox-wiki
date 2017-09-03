## Accessing Plex
1. To access Plex, visit https://plex._yourdomain.com_
2. Login with your Plex account

    ![](https://i.imgur.com/KMVu05O.png)

## First Time Setup

1. When you first login, you will be shown a welcome screen. Click `GOT IT!` to continue.

    ![](https://i.imgur.com/CTG955C.png)

1. Next screen will show you a list of servers, with a randomly generated name. Give it a custom name and click `NEXT`.

    ![](https://i.imgur.com/soGxdGm.png)

1. On the next screen, click `NEXT` (we will add Libraries later).

    ![](https://i.imgur.com/OQxsJd1.png)

1. Click `DONE`.

    ![](https://i.imgur.com/uRr3o61.png)


## Settings

Remote Access

1. Click the Settings icon (top right) -> "Server" (top) -> "Remote Access" (left).

1. Enable `Manually specify public port`, type in `443`, and click the `Retry` or `Apply` button.

1. Click `ENABLE REMOTE ACCESS` (Ignore the "Not available outside your network" message).

    ![](http://i.imgur.com/tq7dzAa.png)

1. Click `SAVE CHANGES`.


Library

1. Click the Settings icon (top right) -> "Server" (top) -> "Library" (left).
1. Disable `Empty trash automatically after every scan` and `Allow media deletion`.
2. Set `Generate video preview thumbnails` and `Generate chapter thumbnails` to `never`.

    ![](http://i.imgur.com/D82n8vh.png)

1. Click `SAVE CHANGES`.

Network

1. Click the Settings icon (top right) -> "Server" (top) -> "Network" (left).
2. Disable `Enable local network discovery (GDM)`.

    ![](http://i.imgur.com/nQXDIUz.png)

1. Click `SAVE CHANGES`.


Transcoder

1. Click the Settings icon (top right) -> "Server" (top) -> "Transcoder" (left).
2. Set `Transcoder default duration` to `150` and `Transcoder default throttle buffer` to `150`.

    ![](https://i.imgur.com/ia8MjvR.png)

1. Click `SAVE CHANGES`.


### DLNA

1. Click the Settings icon (top right) -> "Server" (top) -> "DLNA" (left).

1. Disable `Enable the DLNA server` and `DLNA server timeline reporting`.


    ![](http://i.imgur.com/CLGqMQx.png)

1. Click `SAVE CHANGES`.


### Scheduled Tasks

1. Click the Settings icon (top right) -> "Server" (top) -> "Scheduled Tasks" (left).

    ![](http://i.imgur.com/tjotG75.png)

2. Disable the following:
    - `Update all libraries during maintenance`
    - `Upgrade media analysis during maintenance`
    - `Perform refresh of program guide data`
    - `Analyze and tag photos`.


3. Click `SAVE CHANGES`.


### Extras

1. Click the Settings icon (top right) -> "Server" (top) -> "Extras" (left).

1. Disable `Include Cinema Trailers from movies in my library`.

    ![](http://i.imgur.com/FM7OsPZ.png)

1. Click `SAVE CHANGES`.



## Adding Your First libraries

* Note: the order is important (i.e. Movies first, then TV); or else the config file for Unionfs_cleaner will need to be updated to reflect section ID changes.

### Adding the Movie Library

1. In the main Plex screen (Home icon on the top left), click `+` next to `LIBRARIES`.

    ![](https://i.imgur.com/zadq6ca.png)

1. In the "Add Library" window, select `Movies` and click `NEXT`.

    ![](https://i.imgur.com/UcUFCix.png)

1. Click `BROWSE FOR MEDIA FOLDER`.

    ![](https://i.imgur.com/5kywEro.png)

1. In second column of the "Add Folder" window, select `data`, then `Movies`, and then click the `ADD` button.

    ![ ](https://i.imgur.com/Embc9h9.png)

1. You will now see `/data/Movies` in the text box (don't click `ADD LIBRARY` yet).

    ![](https://i.imgur.com/qzlGMTN.png)

1. Click "Advanced" on the left.

    ![](https://i.imgur.com/4JV0orf.png)

1. Disable the following:
  - `Enable Cinema Trailers`
  - `Enable video preview thumbnails`
  - `Find trailers and extras automatically (Plex Pass required)`

1. Click `ADD LIBRARY`.


### Adding the TV Library

1. In the main Plex screen (Home icon on the top left), click `+` next to `LIBRARIES`.

    ![](https://i.imgur.com/zadq6ca.png)

1. In the "Add Library" window, select `TV Shows` and click `NEXT`.

    ![](https://i.imgur.com/gZtUgtQ.png)

1. Click `BROWSE FOR MEDIA FOLDER`.

    ![](https://i.imgur.com/5kywEro.png)

1. In second column of the "Add Folder" window, select `data`, then `TV`, and then click the `ADD` button.

    ![ ](https://i.imgur.com/Embc9h9.png)

1. You will now see `/data/TV` in the text box (don't click `ADD LIBRARY` yet).

    ![](https://i.imgur.com/i03W0W0.png)

1. Click "Advanced" on the left.

    ![](https://i.imgur.com/JuZif0B.png)

1. Disable the following:
  - `Enable video preview thumbnails`
  - `Find trailers and extras automatically (Plex Pass required)`

1. Click `ADD LIBRARY`.


## Webtools

* If you wish to setup Webtools and install 3rd party add-ons, you can go to https://plex._yourdomain.com_:33400 and login with your Plex account.
