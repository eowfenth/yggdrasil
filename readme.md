# Yggdrasil

<div align="center">A Dockerfile for your Open Ragnarok Dedicated Server</div>

### Roadmap

- [x] Learn how to run a basic server;
- [x] Setup initial commands and inital configuration;
- [ ] Create script to maintenance mode and restart server.
- [ ] Allow usage of MariaDB docker image;
- [ ] Automatized solution to backup;
- [ ] Automatized solution to restore backup;
- [ ] Script to allow usage of metadata instead of manually starting containers; //check gcp-metadata;
- [ ] Start-up script to download, install and start content;
- [ ] Create the instance using yaml;

### Desired Features

- [ ] Server setup via parametrization
- [ ] Kubernetes Setup, a separated pod for each server (Login, Character, Map)
- [ ] Automated setup, almost zero-config.
- [ ] Configuration option for pre-renewal, Hercules and rAthena
- [ ] A pod for the website/panel

### Metadata;

```bash
    $ MYSQL_ROOT_PASSWORD=$(curl http://metadata.google.internal/computeMetadata/v1/instance/attributes/MYSQL_ROOT_PASSWORD -H "Metadata-Flavor: Google") && \
    MYSQL_USER=$(curl http://metadata.google.internal/computeMetadata/v1/instance/attributes/MYSQL_USER -H "Metadata-Flavor: Google") && \
    MYSQL_PASSWORD=$(curl http://metadata.google.internal/computeMetadata/v1/instance/attributes/MYSQL_PASSWORD -H "Metadata-Flavor: Google") && \
    MYSQL_DATABASE=$(curl http://metadata.google.internal/computeMetadata/v1/instance/attributes/MYSQL_DATABASE -H "Metadata-Flavor: Google")
```

### Running the container;

You can run the database with:

```bash
    docker run -p 3306:3306 --name yggdrasil-db -v /var/lib/mysql:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=$MYSQL_ROOT_PASSWORD -e MYSQL_DATABASE=$MYSQL_DATABASE -e MYSQL_USER=$MYSQL_USER -e MYSQL_PASSWORD=$MYSQL_PASSWORD -d serverphobia/yggdrasil-database:0.1.0
```


