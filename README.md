# Argo969 自用备份

这个仓库是 `jane2003` 的自用备份版，复刻自甬哥的 Argosbx 项目。

原项目：https://github.com/yonggekkk/argosbx

保留这个仓库只是为了防止上游仓库以后删除或失效，方便自己继续使用。不是原创项目，也不作为公开推广使用。

## 自用改动

- 主脚本文件名改为 `argo969.sh`。
- 一键命令生成网页改为使用 `jane2003/jonne` 的脚本地址。
- 默认优选域名改为 `1.zbs969.dpdns.org` 到 `10.zbs969.dpdns.org`。
- 生成节点时不再使用 `yg*.ygkkk.dpdns.org`。

## 使用命令

curl：

```bash
bash <(curl -Ls https://raw.githubusercontent.com/jane2003/jonne/main/argo969.sh)
```

wget：

```bash
bash <(wget -qO- https://raw.githubusercontent.com/jane2003/jonne/main/argo969.sh)
```

## 命令生成网页

如果 GitHub Pages 已开启，可以使用：

https://jane2003.github.io/jonne/

## 说明

脚本主体来自原 Argosbx 项目。本仓库只做个人备份和少量自用修改。
