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

```bash
sudo systemctl start docker
sudo systemctl enable docker`
```

[More on service management with systemd](https://fedoraproject.org/wiki/Systemd)
