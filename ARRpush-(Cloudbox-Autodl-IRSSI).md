(Work in Progress)

![](https://i.imgur.com/9EBRiYW.png)



for ipt
i was using
match category
TV/* and Movie/*
if i didnt have the / in movie
it was notifying radarr of XXX/Movie
which ofc i didnt want radarr being told about
so Movie/*
matches all ipt movie cats
and push those to radarr for decision




anyone who has experience with autodl
will know what todo if u just tell them
`sonarr "$(TorrentName)" "$(TorrentUrl)" "$(TorrentSize)" "$(Tracker)"`
as args
and /scripts/arrpush.sh