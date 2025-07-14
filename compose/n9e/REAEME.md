## 夜莺开发环境部署(8.0)

> n9e(nightingale) + vm(victoriametrics)

## 最终目录结构参考

```shell
tree -L .
.
├── compose.yaml
├── config
│   ├── config.toml
│   └── metrics.yaml
├── n9e.db
└── REAEME.md
```

### 官方资料

1. [github仓库](https://github.com/ccfos/nightingale)
2. [中文文档](https://n9e.github.io/zh/)

### 部署流程

> 说明, 尽量减少依赖
> redis 使用的是自带的 miniredis
> 数据库使用的是 sqlite [sql文件](https://github.com/ccfos/nightingale/blob/main/docker/sqlite.sql)

```shell
# 1. 创建工作目录
mkdir n9e && cd n9e
# 2. 下载 sql 文件
curl -s -L https://raw.githubusercontent.com/ccfos/nightingale/main/docker/sqlite.sql -o sqlite.sql
# 3. 导入生成数据库文件
sqlite3 n9e.db < sqlite.sql
# 4. 配置文件目录
mkdir config
```

### 准备配置文件

1. 准备 [compose.yaml](./compose.yaml) 文件

2. 准备 [config.toml](./config/config.toml) 文件

3. 常见指标 [metrics.yaml](./config/metrics.yaml)文件


### 启动 
```shell
docker compose up -d
```

