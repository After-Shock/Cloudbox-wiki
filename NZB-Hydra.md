<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:0 orderedList:0 -->

1. [Accessing NZB Hydra](#1-accessing-nzb-hydra)
2. [Setup](#2-setup)
3. [API](#3-api-key)

<!-- /TOC -->

---


## 1. Accessing NZB Hydra

- To access NZB Hydra, visit https://nzbhydra._yourdomain.com_

## 2. Setup

Enter setup by clicking on "Config" at the top.

1. "Authorization":

    1. Change "Auth type" to `Login form`.

    1. Set all the options below to `ON`.
    1. Click "Add new user". 
    1. Fill in your username and password.
    1. Click "Save" (top right).
    
    ![](https://i.imgur.com/IAxSk4P.png)

 1. Indexers:

    - Add your indexers. Be sure to click "Save" when done.

 1. Downloaders:

    1. "Add new downloader" -> "NZBGet".

    1. Fill in the following:
       - Name: NZBGet
       - Host: `nzbget`
       - Port: `8080`
       - Use SSL: `OFF`
       - Username: [[your NZBGet Username|NZBGet]]
       - Password: [[your NZBGet Password|NZBGet]]
       - Default category: `No category` (verbatim)
       - NZB access type: `Redirect to indexer`
       - NZB adding type: `Upload NZB` (works better than `Send link`) 
  
       ![](https://i.imgur.com/Mn4oJD5.png)

## 3. API Key

To find the NZB Hydra API Key, go to "Config" --> "Main". This will be used later for [[Sonarr|Sonarr#nzb-hydra]] and [[Radarr|Radarr#nzb-hydra]].