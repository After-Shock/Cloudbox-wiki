In the default Cloudbox install, you have two Plex libraries (one for Movies and one for TV Shows). If you would like to have custom libraries in Plex, you may do so as long as the other libraries are located as a sub-directory within the `Movies` folder (e.g. `Movies/Kids`, `Movies/4K`, `Movies/3D`, etc). Below is a guide on how to do this.

_Note: Remember, your Google Drive will have two folders within the `/Media` folder: `Movies` and `TV`. Those are not to be changed and are case sensitive. See [[Prerequisites|Prerequisites#3-google-drive-account]] and [[Paths]] for more info._

_Note 2: You could do the same to TV shows (i.e. have multiple subdirs/libraries within `TV`), but this guide will not go over that. However, the steps are similar to the one below._

## 1. Create folders in Google Drive


Lets say you wanted to have a separate library for 3D, 4K, Hollywood, and Foreign films. You would first have to create these folders in Google Drive. Since all media is located in the `/Media/Movies` folder, you would need to create separate folders for all of these. `/Media/Movies` folder will contain nothing but these folders.

In our example, we will create the following folders: `/Media/Movies/3D`, `/Media/Movies/4k`, `/Media/Movies/Hollywood`, `/Media/Movies/Kids`, and `/Media/Movies/Foreign`.

## 2. Adding Libraries to Plex

You will add each of these folders as separate libraries within Plex (see [[example|Plex#adding-the-movie-library]]). You may name these libraries as whatever you want. The folders will be located in the `/data/Movies` folder.

In our example, this will be: `/data/Movies/3D`, `/data/Movies/4K`, `/data/Movies/Hollywood`, `/data/Movies/Kids`, and `/data/Movies/Foreign`.

## 3. Retrieving Plex Library Section IDs

1. On the server's shell, run the following command:

    ```
    /opt/plex_autoscan/scan.py sections
    ```

1. Your screen will now show something similar to this:

    ```
    1: 3D
    2: 4K
    3: Hollywood
    4: Kids
    5: Foreign
    6: TV
    ```

1. The list here shows your section IDs in the format of `SECTION ID: LIBRARY NAME`. Note: Your section IDs may be different as it is based on the order you added them in Plex.



## 4. Modifying Plex Autoscan

1. On the server's shell, run the following command:

    ```
    nano /opt/plex_autoscan/config/config.json
    ```

1. Scroll down to the `PLEX_SECTION_PATH_MAPPINGS` section.

1. Under this section, you will need to add your section IDs and the library paths (as located in /Media folder in Google Drive). The format is `"SECTION_NUMBER": ["path"]`.

   1. Note: Make sure the path is within quotes (`"/Movies/Kids"`) and there is a comma (`,`) after the close bracket (`]`) - all except the last one (see example below).

1. After the changes, the section will now look similar to this:

   ```
   "PLEX_SECTION_PATH_MAPPINGS": {
      "1": [
          "/Movies/3D/"
      ],
      "2": [
          "/Movies/4K/"
      ],
      "3": [
          "/Movies/Hollywood/"
      ],
      "4": [
         "/Movies/Kids/"
      ],
      "5": [
          "/Movies/Foreign/"
      ],
      "6": [
          "/TV/"
      ]
   },
   ```

1. `Ctrl-X` and `Y` to save.

1. Restart Plex Autoscan: `sudo systemctl restart plex_autoscan`


## 5. Modifying UnionFS Cleaner

1. On the server's shell, run the following command:

    ```
    nano /opt/unionfs_cleaner/config.json
    ```

1. Scroll down to the `rclone_remove_empty_on_upload` section.

1. Change `"/mnt/local/Media/Movies": 1` to `"/mnt/local/Media/Movies": 2`. 

   1. This will tell UnionFS Cleaner to not delete the folders immediately under `/mnt/local/Media/Movies` during cleanup.  

   1. Note: Make sure there is a comma (`,`) at the end of all `"path": #` lines - all except the last one (see example below).

1. After the changes, the section will now look similar to this:

   ```
   "rclone_remove_empty_on_upload": {
       "/mnt/local/Media/Movies": 2,
       "/mnt/local/Media/TV": 1
   },
   ```

1. `Ctrl-X` and `Y` to save.

1. Restart UnionFS Cleaner: `sudo systemctl restart unionfs_cleaner`
