<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:0 orderedList:0 -->

1. [Accessing Plex](#1-accessing-plex)
2. [Setup Wizard](#2-setup-wizard)
3. [Settings](#3-settings)
	- [Remote Access](#remote-access)
	- [Library](#library)
	- [Network](#network)
	- [Transcoder](#transcoder)
	- [DLNA](#dlna)
	- [Scheduled Tasks](#scheduled-tasks)
4. [Adding Your First libraries](#4-adding-your-first-libraries)
	- [Adding the Movie Library](#adding-the-movie-library)
	- [Adding the TV Library](#adding-the-tv-library)
5. [Webtools](#5-webtools)

<!-- /TOC -->

---

## 1. Accessing Plex

1. To access Plex, visit https://plex._yourdomain.com_

2. Login with your Plex account

    ![](https://i.imgur.com/KMVu05O.png)

## 2. Setup Wizard

1. First time you log in, you will be presented with a welcome screen. Click "GOT IT!" to continue.

    ![](https://i.imgur.com/CTG955C.png)

1. Next screen will show you a list of servers, with a randomly generated name. Give it a friendly name and click "NEXT".

    ![](https://i.imgur.com/soGxdGm.png)

1. On the next screen, click "NEXT" (we will add Libraries later).

    ![](https://i.imgur.com/OQxsJd1.png)

1. Click "DONE".

    ![](https://i.imgur.com/uRr3o61.png)


## 3. Settings

### Remote Access

1. Click the Settings icon (top right) -> "Server" (top) -> "Remote Access" (left).

1. Enable "Manually specify public port", type in `443`, and click the "Retry" button. 

1. You will get a "Not available outside your network" message. This is OK. Just click "ENABLE REMOTE ACCESS".

1. Click "SAVE CHANGES".

    ![](http://i.imgur.com/tq7dzAa.png)



### Library

1. Click the Settings icon (top right) -> "Server" (top) -> "Library" (left).

1. Set the following:
   - "Empty trash automatically after every scan": `disabled`
   - "Allow media deletion": `enabled`
   - "Generate video preview thumbnails": `never`
   - "Generate chapter thumbnails": `never`

1. Click "SAVE CHANGES".

    ![](http://i.imgur.com/D82n8vh.png)


### Network

1. Click the Settings icon (top right) -> "Server" (top) -> "Network" (left).

1. Set the following:

   - "Secure Connections": `Preferred`.

   - "Enable local network discovery (GDM)": `disabled`.

1. Click "SAVE CHANGES".

    ![](http://i.imgur.com/nQXDIUz.png)


### Transcoder

1. Click the Settings icon (top right) -> "Server" (top) -> "Transcoder" (left).

2. Set the following:
   - "Transcoder default duration": `150`
   - "Transcoder default throttle buffer": `150`
   - "Use hardware acceleration when available": `enabled`

1. Click "SAVE CHANGES".

    ![](https://i.imgur.com/qvKbH9X.jpg)



### DLNA

1. Click the Settings icon (top right) -> "Server" (top) -> "DLNA" (left).


1. Set the following:
    - "Enable the DLNA server": `disabled`
    - "DLNA server timeline reporting": `disabled`

1. Click "SAVE CHANGES".

    ![](http://i.imgur.com/CLGqMQx.png)



### Scheduled Tasks

1. Click the Settings icon (top right) -> "Server" (top) -> "Scheduled Tasks" (left).


2. Set the following:
    - "Update all libraries during maintenance": `disabled`
    - "Upgrade media analysis during maintenance": `disabled`

3. Click "SAVE CHANGES".

    ![](http://i.imgur.com/tjotG75.png)


## 4. Adding Your First libraries

In this section, we will add two libraries: one for Movies and one for TV.

_Note 1: The order is important (i.e. Movies first, then TV); or else the config file for Plex Autoscan will need to be updated to reflect section ID changes (see [[FAQ|FAQ#if-during-the-first-time-setup-you-switched-the-order-of-plex-libraries-ie-tv-first-then-movies]])._

_Note 2: If you would like to have custom Plex libraries (more than just a Movies and TV one), see [[Customizing Plex Libraries]]._

### Adding the Movie Library

1. In the main Plex screen (Home icon on the top left), click "+" next to "LIBRARIES".

    ![](https://i.imgur.com/zadq6ca.png)

1. In the "Add Library" window, select "Movies" and click "NEXT".

    ![](https://i.imgur.com/UcUFCix.png)

1. Click "BROWSE FOR MEDIA FOLDER".

    ![](https://i.imgur.com/5kywEro.png)

1. In second column of the "Add Folder" window, select `data`, then `Movies`, and then click the "ADD" button.

    ![ ](https://i.imgur.com/Embc9h9.png)

1. You will now see `/data/Movies` in the text box (don't click "ADD LIBRARY" yet).

    ![](https://i.imgur.com/qzlGMTN.png)

1. Click "Advanced" on the left.

1. Set the following:

   - "Enable Cinema Trailers": `disabled` (optional)
   - "Enable video preview thumbnails": `disabled`
   - "Find trailers and extras automatically (Plex Pass required)": `disabled` (optional)

1. Click "ADD LIBRARY".

    ![](https://i.imgur.com/4JV0orf.png)



### Adding the TV Library

1. In the main Plex screen (Home icon on the top left), click "+" next to "LIBRARIES".

    ![](https://i.imgur.com/zadq6ca.png)

1. In the "Add Library" window, select "TV Shows" and click "NEXT".

    ![](https://i.imgur.com/gZtUgtQ.png)

1. Click "BROWSE FOR MEDIA FOLDER".

    ![](https://i.imgur.com/5kywEro.png)

1. In second column of the "Add Folder" window, select `data`, then `TV`, and then click the "ADD" button.

    ![ ](https://i.imgur.com/Embc9h9.png)

1. You will now see `/data/TV` in the text box (don't click "ADD LIBRARY" yet).

    ![](https://i.imgur.com/i03W0W0.png)

1. Click "Advanced" on the left.


1. Set the following:

   - "Enable video preview thumbnails": `disabled`
   - "Find trailers and extras automatically (Plex Pass required)": `disabled` (optional)

1. Click "ADD LIBRARY".


    ![](https://i.imgur.com/JuZif0B.png)




## 5. Webtools

Webtools for Plex comes preinstalled. If you wish to setup Webtools and install 3rd party add-ons, you can go to http://plex._yourdomain.com_:33400 and login with your Plex account.

_Note: Use http://_yourserveripaddress_:33400 if the above URL doesnt work._