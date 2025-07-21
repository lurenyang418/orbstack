# redis 开发环境

```shell
docker run -d --restart=always --name redis -e REDIS_PASSWORD=123456 -p 6379:6379 bitnami/redis

# redis-cli 去警告 --no-auth-warning
redis-cli -h 127.0.0.1 -p 6379 -a 123456 --no-auth-warning ping
```