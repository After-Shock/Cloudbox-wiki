## Setting up Plexdrive Google Drive

1. run this command:

```bash
/opt/plexdrive/plexdrive mount -v 3 --refresh-interval=1m --chunk-check-threads=8 --chunk-load-threads=8 --chunk-load-ahead=4 --max-chunks=250 --fuse-options=allow_other,read_only --config=/opt/plexdrive --cache-file=/opt/plexdrive/cache.bolt /mnt/plexdrive
```


2. 
they type that for plexdrive
it will ask their client id and client secret, visit a link, paste the code
then ctrl + c to stop
then sudo systemctl start plexdrive
and let it do it