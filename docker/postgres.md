---
tags:
  - docker
  - db
  - postgres
---

## Postgres in docker

pull latest postgres
`docker pull postgres:latest`

running postgres db
`docker run -p 5432:5432 --name wwg-postgres-latest -e POSTGRES_PASSWORD=<password here> -d postgres` *dont forget to include the port*


### Accessing postgres from a parallels vm on mac
1) In Parallels, go to Preferences > Advanced > Click the Change Settings... button next to Network > Shared > Show in System Preferences

2) In OS X, find the Parallels Shared connection under System Preferences > Network, copy the IP Address, e.g. 10.211.55.2

3)  In the Windows VM, edit the hosts file, e.g. C:\Windows\System32\drivers\etc\hosts, add an entry for this IP, e.g.
10.211.55.2 vmhost

4) In the Windows VM, add inbound and outbound firewall rules to allow TCP port 5432 

5) Restart the Windows VM
