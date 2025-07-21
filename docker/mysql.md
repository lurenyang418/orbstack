# mysql 开发环境

```shell
# 加上持久化 <data> 目录
# 如果不需要密码 -e ALLOW_EMPTY_PASSWORD=yes 去掉-e MYSQL_ROOT_PASSWORD
docker run -d --restart=always --name mysql -e MYSQL_ROOT_PASSWORD=123456 -p 3306:3306 -v <data>:/bitnami/mysql/data bitnami/mysql:9.3.0
```