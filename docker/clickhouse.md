# clickhouse 


```shell
# 8123 (HTTP 端口)
# 9000 (TCP 端口)
docker run -d --name ch --restart=always -p 8123:8123 -p 9000:9000 -e CLICKHOUSE_ADMIN_PASSWORD=ch123456 bitnami/clickhouse:25

```