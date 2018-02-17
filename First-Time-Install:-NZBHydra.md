

<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:0 orderedList:1 -->

- [Intro](#intro)
- [URL](#URL)
- [Setup](#setup)
- [API](#api-key)

<!-- /TOC -->

## Intro


>NZBHydra is a meta search for NZB indexers. It provides easy access to a number of raw and newznab based >indexers. You can search all your indexers from one place and use it as indexer source for tools like Sonarr or >CouchPotato.

_Note: By default, Cloudbox will install NZBHydra1. Once NZBHydra2 is out of beta, it will be replaced the current one (you may install NZBHydra2 later, if you decide)._ 

## URL

- URL to access NZBHydra: https://nzbhydra._yourdomain.com_

## Setup

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
       - Port: `6789`
       - Use SSL: `OFF`
       - Username: [[Your NZBGet Username|NZBGet]]
       - Password: [[Your NZBGet Password|NZBGet]]
       - Default category: _Leave Blank_ (`No category` doesn't work too well)
       - NZB access type: `Redirect to indexer`
       - NZB adding type: `Upload NZB` (works better than `Send link`) 
  
       ![](https://i.imgur.com/n3ZV0Ki.png)

## API Key

To find the NZBHydra API Key, go to "Config" --> "Main". This will be used later in [[Sonarr|Sonarr#nzbhydra]] and [[Radarr|Radarr#nzb-hydra]].