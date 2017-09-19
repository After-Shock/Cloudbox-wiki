
<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:0 orderedList:1 -->

	1. [Accessing Plex Requests](#1-accessing-plex-requests)
	2. [Admin Account Setup](#2-admin-account-setup)
	3. [Settings](#3-settings)

<!-- /TOC -->

## 1. Accessing Plex Requests

1. To access Plex Requests, visit http://plexrequests._yourdomain_.com


## 2. Admin Account Setup

1. First time you log in, you will be presented with the "Welcome to Plex Requests" screen. Click the orange-colored `admin page` link to be taken to the "Admin" page, then click the `Close` button.

    ![](https://i.imgur.com/nU4LllT.png)

1. You will see the "Sign in" prompt. Click the `Register` link at the bottom.

    ![](https://i.imgur.com/54U1EAA.png)

1. You will now see "Create an Account" prompt. Fill in your preferred `Email` and `Password` and click the `Register` button. This will be the Admin account for Plex Requests.

    ![](https://i.imgur.com/2axV0sW.png)

## 3. Settings

1. You will now be taken to the "General" settings page. You may select whatever options you like here. Click `Update Settings` to save changes.

    ![ ](https://i.imgur.com/02AlzFO.png)

1. On the "Authentication" settings page

    - It is advised to have both `Enable user authentication` and `Require users to login with their passwords` enabled (at the very least `Enable user authentication` enabled).

    - To have your Plex Authorization token automatically retrieved, fill in your `Plex Username` and `Plex Password` and click the `Get Token` button. When this is successful, you will get the "Successfully got token!" message and the `Plex authorization token` textbox will be filled in.

    - Click `Update Settings` to save changes.

    ![ ](https://i.imgur.com/vd35F5e.png)

    ![](https://i.imgur.com/gLucVsz.png)


1. On the "Radarr" settings page:

    - Check "Enable Radarr"

    - "Radarr server IP or Hostname": `radarr`

    - "Radarr server port":`8080`

    - "Radarr API key": _Your Radarr API Key_ (you can find this at [[Radarr|Radarr#1-accessing-radarr]] --> Settings --> General)

    - Click `Update Settings`.

    - Click `Test Radarr server`. The button will update to show "Success!".

    - Click `Get Profiles` and choose your preferred "Download quality profile for Radarr".

    - "Root save directory for movies": `/movies`.

    - Click `Update Settings`.

    ![](https://i.imgur.com/QZCN9S5.png)

1. On the "Sonarr" settings page:

    - Check "Enable Sonarr"

    - "Sonarr server IP or Hostname": `sonarr`

    - "Sonarr server port":`8080`

    - "Sonarr API key": _Your Sonarr API Key_ (you can find this at [[Sonarr|Sonarr#1-accessing-sonarr]] --> Settings --> General)

    - Click `Update Settings`.

    - Click `Test Sonarr server`. The button will update to show "Success!".

    - Click `Get Profiles` and choose your preferred "Download quality profile".

    - "Root save directory for TV shows": `/tv`.

    - Click `Update Settings`.

    ![](https://i.imgur.com/7I0r5E7.png)

1. Click `Sign Out` to exit Settings.
