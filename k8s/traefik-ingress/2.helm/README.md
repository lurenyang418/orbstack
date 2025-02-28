## 使用 helm 

需要通过 cert-manager 来生成证书

```bash
kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.17.1/cert-manager.yaml

# [dnspod(腾讯的) 需要额外的 webhook0(https://cloud.tencent.com/document/product/457/60225)

cat >> webhook.yaml <<EOF
groupName: example.your.domain # 写一个标识 group 的名称，可以任意写
secrets: # 将前面生成的 id 和 token 粘贴到下面
  apiID: "<ID>"
  apiToken: "<Token>"

clusterIssuer:
  enabled: true # 自动创建出一个 ClusterIssuer
EOF

git clone --depth 1 https://github.com/qqshfox/cert-manager-webhook-dnspod.git
helm upgrade --install -n cert-manager -f dnspod-webhook-values.yaml cert-manager-webhook-dnspod ./cert-manager-webhook-dnspod/deploy/cert-manager-webhook-dnspod


cat >> certificate.yaml <<EOF
apiVersion: cert-manager.io/v1
kind: Certificate
metadata:
  name: <example-com-crt>
  namespace: istio-system
spec:
  secretName: <example-com-crt-secret> # 证书保存在这个 secret 中
  issuerRef:
    name: cert-manager-webhook-dnspod-cluster-issuer # 这里使用自动生成出来的 ClusterIssuer
    kind: ClusterIssuer
    group: cert-manager.io
  dnsNames: # 填入需要签发证书的域名列表，确保域名是使用 dnspod 管理的
  - <d.example.com>
  - <w.example.com>

EOF

k apply -f certificate.yaml
```

安装 traefik 

```bash
helm install traefik traefik/traefik -f 1.traefik-value.yaml  --namespace traefik --create-namespace

# 部署 dashboard
k apply -f 2.dashboard.yaml
```

验证

```bash
# 访问 http
curl http://d.example.com -v   # 包含跳转信息  https://d.example.com/dashboard

# 访问 https
curl https://d.example.com -v  # 包含跳转信息  https://d.example.com/dashboard
```