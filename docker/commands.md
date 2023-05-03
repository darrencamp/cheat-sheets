---
tags:
  - docker
---

## Copy from docker image
`docker cp [OPTIONS] CONTAINER:SRC_PATH DEST_PATH|-`

## using Azure container registry
`docker login --name <registry-name>`

TODO: docker login for azure container registry, with login token
TODO: push to Azure CR


## login as root
docker exec -u 0 -it <container-name> /bin/bash