## 1. Accessing Jackett

 - To access Jackett, visit http://jackett._yourdomain.com_

## 2. Settings
  
   ![](https://i.imgur.com/CAHMsfH.png)


### Setting Admin password

Under "Jackett Configuration": 

1. Set "Admin password" to your preferred password.

1. Click "Set Password".

1. Jackett will now refresh and ask you to log in with your admin password.

   ![](https://i.imgur.com/hRJr1Fh.png)

### Disabling Auto Update

Under "Jackett Configuration": 

1. Check "Disable auto update".

1. Check "External access".

1. Click "Apply server settings". 

1. The page will now reload.  




## 3. Adding Indexers to Sonarr/Radarr

Under "Configured Indexers":

1. Click "Add Indexer" to add your preferred indexers (i.e. torrent trackers). 

1. When adding indexers into [[Sonarr|Sonarr#jackett]]/[[Radarr|Radarr#jackett]], you will need: 

    1. Indexer's Torznab Feed. 

         - Copy this by clicking on "Copy Torznab Feed" button next to the Indexer. You will need to Replace `https` with `http` and replace `jackett.yourdomain.com` with `jackett:8080`.

    1. Jacket API Key

