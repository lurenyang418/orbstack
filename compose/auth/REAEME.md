## tinyauth + traefik 使用

[配置说明](https://tinyauth.app/docs/reference/configuration)

- Github OAuth
- Google OAuth
- 自定义 OAuth
- LDAP
- 账号密码


本地测试, 需要添加如下域名解析至 `/etc/hosts`

```plaintext
127.0.0.1 example.com
127.0.0.1 tinyauth.example.com
127.0.0.1 whoami.example.com
```

浏览器如果出现 `502` . 记得关闭代理软件
