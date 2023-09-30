## Docker inspect

Provides more details about a container than the `docker ps` command. It returns these details in Json format.

```
> docker inspect <container id> 
```

## Docker logs

Provides the logs for the container. Especially usefully if the container is running on detached mode.

```
> docker run --name db -e POSTGRES_PASSWORD=password -d postgres:15-alpine   

> docker ps
CONTAINER ID   IMAGE                COMMAND                  CREATED        STATUS                            PORTS                    NAMES
7468761c4be3   postgres:15-alpine   "docker-entrypoint.s…"   24 hours ago   Up 6 seconds (health: starting)   0.0.0.0:5432->5432/tcp   db

> docker logs db

PostgreSQL Database directory appears to contain a database; Skipping initialization

2023-09-29 18:24:34.785 UTC [1] LOG:  starting PostgreSQL 15.4 on aarch64-unknown-linux-musl, compiled by gcc (Alpine 12.2.1_git20220924-r10) 12.2.1 20220924, 64-bit
2023-09-29 18:24:34.786 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2023-09-29 18:24:34.786 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2023-09-29 18:24:34.805 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2023-09-29 18:24:34.817 UTC [25] LOG:  database system was interrupted; last known up at 2023-09-28 18:00:29 UTC
2023-09-29 18:24:36.930 UTC [25] LOG:  database system was not properly shut down; automatic recovery in progress
2023-09-29 18:24:36.958 UTC [25] LOG:  redo starts at 0/B026960
2023-09-29 18:24:36.966 UTC [25] LOG:  unexpected pageaddr 0/9032000 in log segment 00000001000000000000000B, offset 204800
2023-09-29 18:24:36.966 UTC [25] LOG:  redo done at 0/B0306C0 system usage: CPU: user: 0.00 s, system: 0.00 s, elapsed: 0.00 s
2023-09-29 18:24:36.970 UTC [23] LOG:  checkpoint starting: end-of-recovery immediate wait
2023-09-29 18:24:36.983 UTC [23] LOG:  checkpoint complete: wrote 12 buffers (0.1%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.007 s, sync=0.001 s, total=0.014 s; sync files=10, longest=0.001 s, average=0.001 s; distance=45 kB, estimate=45 kB
2023-09-29 18:24:36.988 UTC [1] LOG:  database system is ready to accept connections 
```
