rac2@Rodrigos-MacBook-Pro digital-cloud-training % docker run -d ubuntu sleep 100
ebb51dad7d7b390140d9f0ac46d4c168a45c3c48ff968640078feeb6e90c2519
rac2@Rodrigos-MacBook-Pro digital-cloud-training % docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED         STATUS         PORTS     NAMES
ebb51dad7d7b   ubuntu    "sleep 100"   4 seconds ago   Up 4 seconds             lucid_dirac
rac2@Rodrigos-MacBook-Pro digital-cloud-training % docker exec lucid_dirac cat /etc/hosts
127.0.0.1	localhost
::1	localhost ip6-localhost ip6-loopback
fe00::0	ip6-localnet
ff00::0	ip6-mcastprefix
ff02::1	ip6-allnodes
ff02::2	ip6-allrouters
172.17.0.2	ebb51dad7d7b

