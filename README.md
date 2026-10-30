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

## 更新说明

手动更新的命令
先分清两件事：脚本本体不会自动更新（启动参数带 --no-autoupdate，且脚本只在 cloudflared 不存在时才下载），
所以“更新脚本”和“更新 cloudflared 内核”是两条路。

第一步：确认 VPS 上装的是哪一份

grep -m1 -o 'jane2003/jonne\|yonggekkk/argosbx' /root/bin/agsbx

情况一：输出 jane2003/jonne，且脚本已覆盖成新版 → 直接

agsbx upa

情况二：不想动已装脚本，直接用仓库最新版跑一次（新脚本带 upa 逻辑，跑完不留痕）

cd ~ && bash <(curl -Ls https://raw.githubusercontent.com/jane2003/jonne/main/argo969.sh) upa

这条验证过：upa 参数能正确传进脚本并进入 upa 分支。

情况三：完全不用脚本，三条裸命令

curl -fLo /root/agsbx/cloudflared.new https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64

chmod +x /root/agsbx/cloudflared.new && /root/agsbx/cloudflared.new version

mv -f /root/agsbx/cloudflared.new /root/agsbx/cloudflared && systemctl restart argo

更新后怎么确认

/root/agsbx/cloudflared version          # 应为 2026.10.5

systemctl status argo --no-pager | head -5

journalctl -u argo -n 30 --no-pager | grep 'Registered tunnel connection'
