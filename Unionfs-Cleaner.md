WORK IN PROGRESS

---

Unionfs_Cleaner comes pre-set for the default paths used by cloudbox (refer to paths section).

If you are using subdirecties within the default paths (e.g. Media/Movies/Kids etc) then this will also be caught / uploaded.

the default configuration can be found at /opt/unionfs_cleaner/config.json - if you wish to receive notifications, edit that file and put in your pushover app token and pushover user token, save it and then it will restart itself, so dont worry about restarting it. notifications will be sent when uploads begin / skipped due to files being accessed / upload cancelled due to ban/interval restored after a ban sleep of 25hrs has completed).

the default local content max size / check interval can be edited whenever via changing them in that configuration file and saving it causing unionfs_cleaner to reload itself.

if you want to know more about each configuration setting, read the readme @ github.com/l3uddz/unionfs_cleaner