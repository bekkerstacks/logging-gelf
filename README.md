# logging-gelf

Logging with Logstash, Elasticsearch, Kibana

## Usage

Get the sources:

```
$ git clone https://github.com/bekkerstacks/logging-gelf
$ cd logging-gelf
```

Get traefik:

```
$ wget -O docker-compose.traefik.yml \
  https://raw.githubusercontent.com/bekkerstacks/traefik/master/docker-compose.yml
```

Deploy Traefik and the Logging Stack:

```
$ docker stack deploy -c docker-compose.traefik.yml proxy
$ docker stack deploy -c docker-compose.yml logging
```

## Configuration

Forwarding stdout logs to gelf driver:

```
    logging:
      driver: gelf
      options:
        gelf-address: udp://localhost:12201
        tag: production
```

## Endpoints:

Access Kibana:

- Kibana: `http://kibana.${DOMAIN}`

## Resources

- https://blog.docker.com/2017/02/adventures-in-gelf/
- https://gist.github.com/eunomie/e7a183602b8734c47058d277700fdc2d
