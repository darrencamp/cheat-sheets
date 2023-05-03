---
tags:
  - macos
---

# Useful Mac things to remember

## zip up a folder
macOS has tar installed by default. The following command will tar and gzip a folder. 

What does tar mean: tape archive :) 
What about the options: 
* c: creates archive
* z: compress using gzip
* f: creates archive with given filename
* v: optional, verbose output

```bash
tar czvf file_name.tar.gz folder_to_compress
```

## unzip a folder

```bash
tar -xvf file_name.tar.gz -C destination_foler
```

or create a zipfile
## create a zip file
```
zip -r -X archive_name.zip folder_to_compress
```

## unzip
```
unzip archive_name.zip
```

### find process listening on a port
https://stackoverflow.com/questions/4421633/who-is-listening-on-a-given-tcp-port-on-mac-os-x

`sudo lsof -nP -i4TCP:$PORT | grep LISTEN`

where $PORT is the port number 

