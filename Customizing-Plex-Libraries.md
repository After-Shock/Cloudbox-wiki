<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:0 orderedList:0 -->

- [Intro](#intro)
- [Scenario 1](#scenario-1) (recommended; somewhat user-friendly)
- [Scenario 2](#scenario-2) (not recommended; a bit more complicated; requires modifying Radarr/Sonarr root paths)

<!-- /TOC -->

---




## Intro

In the default Cloudbox install, there only two main Plex libraries: one for Movies and one for TV Shows. With the idea that all movies are to be placed within the `/Media/Movies` folder in Google Drive.


Default Paths:



   ```
   Media
   ├── Movies
   └── TV
   ```



If you would like to have custom libraries in Plex, you may do so with this guide. But regardless of what scenario you choose below, the content will always be located within `/Media` folder in Google Drive (i.e. `/mnt/unionfs/Media` on the server). 

<br />



> For those that that are interested, here is a generalized version of my library setup, which is based on Scenario 1.  
>
> ```
> Media
> ├── Movies
> │   ├── Movies
> │   ├── Movies-3D
> │   ├── Movies-Anime
> │   ├── Movies-Kids
> │   ├── Movies-Remux-HD
> │   ├── Movies-Remux-UHD
> │   ├── Other-Documentaries
> │   ├── Other-FanFilms
> │   └── Other-Standup-Comedy
> ├── Music
> └── TV
> ```
>
> "Movies/Movies" is my main movies folder (mostly Hollywood films and a few misc foreign ones). <br />
> "Movies/Movies-Kids" folder is for family rated, animated films. 

<br />

## Scenario 1

You want to place your libraries within the `/Media/Movies` folder.


Example:

```
Media
├── Movies
│   ├── 3D
│   ├── 4K
│   ├── Foreign
│   ├── Hollywood
│   └── Kids
└── TV

```




_Note: You could do the same to TV shows (i.e. have multiple sub-dirs within `TV`), but this guide will not go over that. However, the steps are similar to the ones below._



### 1. Create Folders in Google Drive


Let's say you wanted to have separate movie libraries for: 3D, 4K, Foreign, Hollywood, and Kids. You would first have to create these folders within the `/Media/Movies` path in Google Drive. `/Media/Movies` folder will contain nothing but these folders. 

_Note: Remember, folders are case sensitive in Google Drive and in Linux (e.g. `4K` and `4k` are 2 different folders)._

In our example, we will create the following folders: `/Media/Movies/3D`, `/Media/Movies/4K`, `/Media/Movies/Foreign`, `/Media/Movies/Hollywood`, and `/Media/Movies/Kids`.

![](https://i.imgur.com/uze7hRK.png)

### 2. Add Libraries to Plex

You will add each of these folders as separate libraries within Plex (see [[example|First-Time-Install: Plex#adding-the-movie-library]]). You may name these libraries as whatever you want. The folders will be located in the `/data/Movies` folder.

In our example, this will be: `/data/Movies/3D`, `/data/Movies/4K`, `/data/Movies/Foreign`, `/data/Movies/Hollywood`, and `/data/Movies/Kids`.

### 3. Retrieve Plex Library Section IDs

 - See [[Plex Library Section IDs]].


### 4. Modify Plex Autoscan Config

_Note: If you have a separate Plex and Feeder setup, this will be done on the server where Plex is installed._

1. On the server's shell, run the following command:

    ```
    nano /opt/plex_autoscan/config/config.json
    ```

1. Scroll down to the `PLEX_SECTION_PATH_MAPPINGS` section.

    1. Under this section, you will need to add your section IDs and the library paths (as located within the `/Media` folder in Google Drive). 

       The format will look like:

       ```json
       "SECTION_NUMBER": [
           "/Movies/<folderpath>/"
       ],
       ```

       Note 1: Make sure the folder paths are within quotes (e.g. `"/Movies/3D"`) and there is a comma (`,`) after the close bracket (`]`) - all except the last one (see example below).

       Note 2: Since folders are case sensitive, make sure the folder path matches the same case as the folders you created in Google Drive (e.g. `"/Movies/4K"` is not the same as `"/Movies/4k"`).

    1. After the changes, the section will now look similar to this:

       ```json
       "PLEX_SECTION_PATH_MAPPINGS": {
          "1": [
              "/Movies/3D/"
          ],
          "2": [
              "/Movies/4K/"
          ],
          "3": [
              "/Movies/Foreign/"
          ],
          "4": [
              "/Movies/Hollywood/"
          ],
          "5": [
              "/Movies/Kids/"
          ],
          "6": [
              "/TV/"
          ]
       },
       ```

1. `Ctrl-x`, `y`, and `enter` to save.


1. Restart Plex Autoscan: `sudo systemctl restart plex_autoscan`


_Note: Do not modify `SERVER_PATH_MAPPINGS` as this does not require any changes._

### 5. Modify UnionFS Cleaner Config

_Note: If you have a separate Plex and Feeder setup, this will be done on the server where Feederbox is setup._

1. On the server's shell, run the following command:

    ```
    nano /opt/unionfs_cleaner/config.json
    ```

1. Scroll down to the `rclone_remove_empty_on_upload` section.

1. Change `"/mnt/local/Media/Movies": 1` to `"/mnt/local/Media/Movies": 2`. 

   1. This will tell UnionFS Cleaner to not remove empty folders directly under `/mnt/local/Media/Movies` during cleanup.  

   1. Note: Make sure there is a comma (`,`) at the end of all `"path": #` lines - all except the last one (see example below).

1. After the changes, the section will now look similar to this:

   ```json
   "rclone_remove_empty_on_upload": {
       "/mnt/local/Media/Movies": 2,
       "/mnt/local/Media/TV": 1
   },
   ```

1. `Ctrl-x`, `y`, and `enter` to save.

1. UnionFS Cleaner will restart itself when it detects config.json has changed.


### 6. Change Root Paths in Radarr

Set your Movie Paths in [[Radarr|First-Time-Install: Radarr#8-adding-the-movies-path]] to reflect the new sub-dirs (e.g. `/movies/3D`).

### 7. Change Root Paths in Plex Requests

Set the default "Root save directory for movies" on the Radarr setup page of [[Plex Requests|First Time Install: Plex-Requests#3-settings"Root save directory for movies"]] (e.g. `/movies/3D`).

***

## Scenario 2

You want to place your libraries within the `/Media` folder.


Example:

```
Media
├── Movies-3D
├── Movies-4K
├── Movies-Foreign
├── Movies-Hollywood
├── Movies-Kids
└── TV

```




_Note: You could do the same to TV shows, but this guide will not go over that. However, the steps are similar to the ones below._



### 1. Create Folders in Google Drive


Let's say you wanted to have separate movies libraries for: general movies folder, 3D, 4K, Foreign, Hollywood, and Kids. You would first have to create these folders within the `/Media` path in Google Drive. `/Media/` folder will contain nothing but these folders (and the `TV` folder).

_Note: Remember, folders are case sensitive in Google Drive and in Linux (e.g. `4K` and `4k` are 2 different folders)._

In our example, we will create the following folders: `/Media/Movies-3D`, `/Media/Movies-4K`, `/Media/Movies-Foreign`, `/Media/Movies-Hollywood`, and `/Media/Movies-Kids`.


![](https://i.imgur.com/nM1bCxm.png)

### 2. Add Libraries to Plex

You will add each of these folders as separate libraries within Plex (see [[example|First-Time-Install: Plex#adding-the-movie-library]]). You may name these libraries as whatever you want. The folders will be located in the `/data` folder.

In our example, this will be: `/data/Movies-3D`, `/data/Movies-4K`, `/data/Movies-Foreign`, `/data/Movies-Hollywood`, and `/data/Movies-Kids`.


### 3. Retrieve Plex Library Section IDs

 - See [[Plex Library Section IDs]].


### 4. Modify Plex Autoscan Config

_Note: If you have a separate Plex and Feeder setup, this will be done on the server where Plex is installed._

1. On the server's shell, run the following command:

    ```
    nano /opt/plex_autoscan/config/config.json
    ```

1. Scroll down to the `PLEX_SECTION_PATH_MAPPINGS` section.

   1. Under this section, you will need to add your section IDs and the library paths (as located within the `/Media` folder in Google Drive).


       The format will look like:

       ```json
       "SECTION_NUMBER": [
           "/<folder>/"
       ],
       ```

       Note 1: Make sure the folder paths are within quotes (e.g. `"/Movies-3D"`) and there is a comma (`,`) after the close bracket (`]`) - all except the last one (see example below).

       Note 2: Since folders are case sensitive, make sure the folder path matches the same case as the folders you created in Google Drive (e.g. `"/Movies-4K"` is not the same as `"/Movies-4k"`).

   1. After the changes, the section will now look similar to this:

       ```json
       "PLEX_SECTION_PATH_MAPPINGS": {
          "1": [
              "/Movies-3D/"
          ],
          "2": [
              "/Movies-4K/"
          ],
          "3": [
              "/Movies-Foreign/"
          ],
          "4": [
              "/Movies-Hollywood/"
          ],
          "5": [
              "/Movies-Kids/"
          ],
          "6": [
              "/TV/"
          ]
       },
       ```


1. Scroll down to the `SERVER_PATH_MAPPINGS` section.

    1. Under this section, you will need to add library paths (as seen from within Plex) with the corresponding `/mnt/unionfs/Media/` path. 

        The format will look like:

        ```json
        "/data/<folder>": [
          "/mnt/unionfs/Media/<folder>"
        ],
        ```

       Note: Make sure the folder paths are within quotes (e.g. `"/data/Movies-3D/"`) and there is a comma (`,`) after the close bracket (`]`) - all except the last one (see example below).

    1. After the changes, the section will now look similar to this:


        ```json
        "SERVER_PATH_MAPPINGS": {
          "/data/Movies-3D/": [
            "/mnt/unionfs/Media/Movies-3D/"
          ],
          "/data/Movies-4K/": [
            "/mnt/unionfs/Media/Movies-4K/"
          ],
          "/data/Movies-Foreign/": [
            "/mnt/unionfs/Media/Movies-Foreign/"
          ],
          "/data/Movies-Hollywood/": [
            "/mnt/unionfs/Media/Movies-Hollywood/"
          ],
          "/data/Movies-Kids/": [
            "/mnt/unionfs/Media/Movies-Kids/"
          ],
          "/data/TV/": [
            "/tv/",
            "/mnt/unionfs/Media/TV/"
          ]
        },
        ```


1. `Ctrl-x`, `y`, and `enter` to save.


1. Restart Plex Autoscan: `sudo systemctl restart plex_autoscan`


### 5. Modify UnionFS Cleaner Config

_Note: If you have a separate Plex and Feeder setup, this will be done on the server where Feederbox is setup._

1. On the server's shell, run the following command:

    ```
    nano /opt/unionfs_cleaner/config.json
    ```

1. Scroll down to the `rclone_remove_empty_on_upload` section.

1. Add the paths under it. (e.g. `"/mnt/local/Media/Movies-3D": 1`)

   1. This will tell UnionFS Cleaner to not remove empty folders directly under `/mnt/local/Media/Movies` during cleanup.  

   1. Note: Make sure there is a comma (`,`) at the end of all `"path": #` lines - all except the last one (see example below).

1. After the changes, the section will now look similar to this:

   ```json
   "rclone_remove_empty_on_upload": {
       "/mnt/local/Media/Movies-3D": 1,
       "/mnt/local/Media/Movies-4K": 1,
       "/mnt/local/Media/Movies-Foreign": 1,
       "/mnt/local/Media/Movies-Hollywood": 1,
       "/mnt/local/Media/Movies-Kids": 1,
       "/mnt/local/Media/TV": 1
   },
   ```

1. `Ctrl-x`, `y`, and `enter` to save.

1. UnionFS Cleaner will restart itself when it detects config.json has changed.


### 6. Change Root Paths in Radarr

Set your Movie Paths in [[Radarr|First-Time-Install: Radarr#8-adding-the-movies-path]] to reflect the new sub-dirs (e.g. `/mnt/unionfs/Media/Movies-3D`).


### 7. Change Root Paths in Plex Requests

Set the default "Root save directory for movies" on the Radarr setup page of [[Plex Requests|First Time Install: Plex-Requests#3-settings"Root save directory for movies"]] (e.g. `/mnt/unionfs/Media/Movies-3D`).