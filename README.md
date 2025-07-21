# orbstack 使用指南

## 1. [docker](./docker)

## 2. [compose](./compose)

## 3. [k8s](./k8s)

### 1. kubectl 插件管理 [krew](https://krew.sigs.k8s.io/)

安装 `krew`
```shell
brew install krew
```

推荐插件

    1. ctx
    2. iexec 

安装插件
```shell

k krew install iexec
```

### 2. 包管理 [helm](https://github.com/helm/helm)

```shell
brew install helm
```