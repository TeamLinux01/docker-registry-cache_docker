# How to setup docker registry cache docker container, a docker registry caching service

* Please copy the .env.example to .env and edit the values before running docker-compose up.
* Create or edit /etc/docker/daemon.json

```json
  {
    "registry-mirrors": ["https://docker-registry-cache.hostname.domainname"]
  }
```

* systemctl restart docker.service
