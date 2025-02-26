# orbstack ingress-nginx 安装

## 安装 ingress-nginx

```bash
# 官方提供的 yaml 是 deployment 形式部署的， 这里改成了 daemon set 形式, 具体看 yaml 中的注释
kubectl apply -f daemonset.yaml
```

## 测试 http 服务

```bash
kubectl apply -f nginx
# 在 /etc/hosts 中添加域名解析
# 127.0.0.1 web.example.com

# 访问 http://web.example.com
# 如果出现无法访问(502 Bad Gateway), 请确认是否开启 clash 之类的代理, 临时关闭
unset http_proxy
curl http://web.example.com -v
```

## 测试 tcp 服务(redis)

```bash
# 注意 tcp-services.yml 中的 metadata.name 与 daemonset.yaml 中的 tcp 代理部分一致
kubectl apply -f redis
# 在 /etc/hosts 中添加域名解析
# 127.0.0.1 web.example.com

redis-cli -h redis.example.com -p 6379 -a redis6379 --no-auth-warning ping
```