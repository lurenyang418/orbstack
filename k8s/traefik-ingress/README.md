# 部署 traefik-ingress

```bash
kubectl apply -f 1.rbac.yaml
kubectl apply -f 2.traefik.yaml

# 域名映射暴露 dashboard
echo 127.0.0.1 dashboard.example.com  | sudo tee -a /etc/hosts > /dev/null
```

## 部署个 [whoami](https://github.com/traefik/whoami)

```bash
kubectl apply -f example

# 域名映射暴露 whoami
echo 127.0.0.1 whoami.example.com  | sudo tee -a /etc/hosts > /dev/null
```

