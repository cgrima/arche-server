## Docker Group
---
Create Docker group and add current user:

```sh
sudo groupadd docker
sudo useradd -G docker ${USER}
```


## Docker Daemon
---

Start the Docker daemon and enable automatic startup at boot:

```sh
sudo systemctl start docker
sudo systemctl enable docker
```

[More on service management with systemd](https://fedoraproject.org/wiki/Systemd)



## Docker/Firewalld incompatibility
---

Disable firewalld to avoid issues like `503 error` on docker container access via http

```sh
sudo systemctl stop firewalld.service
sudo systemctl disable firewalld.service
systemctl mask firewalld
```
