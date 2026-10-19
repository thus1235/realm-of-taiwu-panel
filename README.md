# Realm of Taiwu 修改器 · 更新源

这个仓库只做一件事：给修改器的**自动更新**提供「最新版本清单 + exe 直链」。

## 文件

| 文件 | 作用 |
|---|---|
| `update.json` | 更新清单：版本号、exe 直链（GitHub raw + jsDelivr 双源）、sha256、更新说明 |
| `Realm-of-Taiwu.exe` | 最新版主程序本体 |

## 客户端怎么用

修改器启动 4 秒后读取 `update.json`：

- 版本比本机新 → 标题栏显示 `v旧 → v新`，点「更新」即可一键下载替换并重启
- 已是最新 → 什么都不做

程序里内置了两个清单地址（先 raw 后 jsDelivr），任意一个能通即可。

## 怎么发新版

在修改器工程目录执行：

```
python 工具\发布更新.py "这次改了什么"
```

脚本会：复制新 exe → 重算 sha256 → 重写 `update.json` → commit → push。
推送成功后 1~2 分钟内所有客户端就能看到新版本。

> 换版本号记得同步 `RealmOfTaiwuPanel.csproj` 里的 `<Version>`：客户端就是拿它比大小的。
