# etcd

```shell
docker run --restart=always -d --name etcd \
    -p 2379:2379 \
    -p 2380:2380 \
    -e ALLOW_NONE_AUTHENTICATION=yes \
    -e ETCD_ADVERTISE_CLIENT_URLS=http://127.0.0.1:2379 \
    bitnami/etcd:latest
```