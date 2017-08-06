dont touch transcodes folder. 



it wont be wiped at system reboot like /tmp to /dev/shm
(ram)

the issue was the folder being deleted on reboot. causing docker to create the temporary lex transcode folder as root. causing the transcoder to crash as it had no permissions
u cud mention that somehow
e.g. for plex transcodes set a permanant location that isnt wiped after a reboot (e.g. /tmp or /dev/shm)