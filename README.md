# minas-appstore-catalog

MINAS 私有应用商店**官方货架**（应用目录数据仓）：小米 NAS（小米智能存储）米家「应用中心」里可一键安装的第三方应用清单。纯数据——`catalog.json` + `icons/`，上新一款应用不需要动引擎。

配套引擎：[mizuka-wu/minas-appstore](https://github.com/mizuka-wu/minas-appstore)（单 Go 二进制，Docker 安装事务 + 应用中心自动注册 + 自愈）

## 已上架应用

| 应用 | 用途 |
|---|---|
| qBittorrent | BT/PT 下载 |
| Jellyfin | 免费开源媒体库 |
| Emby | 媒体库 |
| Home Assistant | 智能家居中枢 |
| Homebridge (+miot) | 把米家设备接入 HomeKit |
| AList | 网盘聚合挂载 |
| AniRSS | 追番订阅 |
| Cloudflare Tunnel | 内网穿透（免公网 IP 远程访问） |

## 作为用户

在你的商店 unit 里订阅本货架：

```
CATALOG_SOURCES=github:mizuka-wu/minas-appstore-catalog@main
```

想覆盖某款应用的配方？把自己的货架源排在后面（同名条目后者覆盖前者）。

## 作为作者（上架你的应用）

1. 照着 [docs/manifest.md](https://github.com/mizuka-wu/minas-appstore/blob/main/docs/manifest.md) 写一条应用配方
2. 图标规格 300×300 PNG，放进 `icons/`
3. 提 PR——描述里带上你的应用是干什么的、需要哪些端口/环境变量即可

## 为什么要自建商店

小米 NAS 官方应用商店没有第三方入口。本项目逆向了米家应用中心的本地注册机制（注册表 + 农场软链 + nginx 子配置），让任意 Docker 应用都能"伪装"成官方应用获得卡片入口——详见引擎仓 README 的原理章节。
