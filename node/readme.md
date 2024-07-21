# Setting up nodes to connect to existing grafana and loki 

Change Loki:3100 to IP:port of the serve in `promtail.yaml`. 

Do `docker compose up -d` only in `node` folder (not the main docker-compose file).

# install docker compose plugin

https://grafana.com/docs/loki/latest/send-data/docker-driver/

https://grafana.com/docs/loki/latest/send-data/docker-driver/configuration/

add this to daemon.json:

```
{
    "debug" : true,
    "log-driver": "loki",
    "log-opts": {
        "loki-url": "https://ip:port/loki/api/v1/push",
        "loki-batch-size": "400"
    }
}
```

After that restart docker service. 