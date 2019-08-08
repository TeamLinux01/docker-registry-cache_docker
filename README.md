# How to setup docker registry cache docker container, a docker registry caching service

* Please copy the .env.example to .env and edit the values before running docker-compose up.
* Create or edit /etc/docker/daemon.json

```json
  {
    "registry-mirrors": ["https://docker-registry-cache.hostname.domainname"]
  }
```

* systemctl restart docker.service

## Use Self-Signed SSL cert

* Create the follow folders if they are missing on the client (**must be root to write these folders and files**)
  * /etc/docker/certs.d/*server-name*:*port*
* Copy the .crt file into /etc/docker/certs.d/*server-name*:*port*
  * rsync -azv *user*@*server*:/*folder*/*to*/*cert*.crt .
  * sudo cp -la *cert*.crt /etc/docker/certs.d/*server-name*:*port*/
    * This will copy the cert file, which must be the named exactly the same as the server url, from your server to the current directory and then create a hard-link copy to docker certs
    * If the name of the sever was **registry.server.local**, then the cert would be called **registry.server.local.crt**
    * If there is a bundled cert file, please use that one.
