# Deliverables

## The commands you used to diagnose the problem

```bash
~/repositories/github/maor-klir/kubecraft/lessons/clab/01-containerlab-primer main*
❯ docker exec -it clab-first-lab-srl2 sr_cli
Error response from daemon: container d8775d9fc6c8cd08a5860569463d191d1ac24bfe154ae3de7fb3d9148e3cc905 is not running

~/repositories/github/maor-klir/kubecraft/lessons/clab/01-containerlab-primer main*
❯ docker ps -a --filter name=clab-first-lab
CONTAINER ID   IMAGE                           COMMAND                  CREATED         STATUS                            PORTS     NAMES
d8775d9fc6c8   ghcr.io/nokia/srlinux:24.10.1   "/tini -- fixuid -q …"   2 minutes ago   Exited (143) About a minute ago             clab-first-lab-srl2
738eb44957d1   ghcr.io/nokia/srlinux:24.10.1   "/tini -- fixuid -q …"   2 minutes ago   Up 2 minutes                                clab-first-lab-srl1

~/repositories/github/maor-klir/kubecraft/lessons/clab/01-containerlab-primer main*
❯ containerlab inspect -t topology/lab.clab.yml
14:53:20 INFO Parsing & checking topology file=lab.clab.yml
╭─────────────────────┬───────────────────────────────┬─────────┬───────────────────╮
│         Name        │           Kind/Image          │  State  │   IPv4/6 Address  │
├─────────────────────┼───────────────────────────────┼─────────┼───────────────────┤
│ clab-first-lab-srl1 │ srl                           │ running │ 172.20.20.7       │
│                     │ ghcr.io/nokia/srlinux:24.10.1 │         │ 3fff:172:20:20::7 │
├─────────────────────┼───────────────────────────────┼─────────┼───────────────────┤
│ clab-first-lab-srl2 │ srl                           │ exited  │ N/A               │
│                     │ ghcr.io/nokia/srlinux:24.10.1 │         │ N/A               │
╰─────────────────────┴───────────────────────────────┴─────────┴───────────────────╯
```

## How you fixed it

```bash
~/repositories/github/maor-klir/kubecraft/lessons/clab/01-containerlab-primer main*
❯ docker start clab-first-lab-srl2
clab-first-lab-srl2
```

## Why `docker ps` alone wouldn't show the stopped container

`docker ps` will only show running containers.  
`docker ps -a` will also show any stopped containers.
