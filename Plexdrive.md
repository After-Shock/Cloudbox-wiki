```
/opt/plexdrive/plexdrive mount -v 3 --refresh-interval=1m --max-chunks=250 --fuse-options=allow_other,read_only --config=/opt/plexdrive --cache-file=/opt/plexdrive/cache.bolt /mnt/plexdrive
```
they type that for plexdrive
it will ask their client id and client secret, visit a link, paste the code
then ctrl + c to stop
then sudo systemctl start plexdrive
and let it do it