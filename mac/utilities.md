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