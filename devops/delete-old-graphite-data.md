# Delete old graphite data

Sometimes you want to delete some old data in graphite. Since graphite uses whisper as a storage mechanism everything is 
just files on the files system. In the commands below it is assumed that your data is stores under `/opt/graphite/storage/whisper`. 
This will delete all data older then 90 days.

See how much disk space will be freed up:
```bash
    find /opt/graphite/storage/whisper/ -name "*wsp" -mtime +90 -exec echo -n -e {}"\0" \; | du -hc --files0-from=-
```

Delete the files

```bash
   find /opt/graphite/storage/whisper/ -type f -mtime +90 -name "*wsp" -exec rm '{}' \;
```