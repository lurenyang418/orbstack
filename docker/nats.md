# nats

```shell
# 4222 客户端
# 8222 http监控
# 6222 集群
docker run --restart=always -d  --name nats \
 -p 4222:4222 \
 -p 8222:8222 \
 bitnami/nats --http_port 8222

# brew install nats
nats account info -s "http://127.0.0.1:4222"
```
