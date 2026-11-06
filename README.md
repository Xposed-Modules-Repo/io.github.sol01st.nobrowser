# 不用内置浏览器打开 · ExLink-NoBrowser

一个 LSPosed 模块：在微信、QQ、TIM、QQ邮箱、钉钉、百度贴吧等应用里点击链接时，把链接从应用内置浏览器里抢出来，交给你自己的浏览器打开。

测试环境 HyperOS4 Android17

基于 [xloger/ExLink](https://github.com/xloger/ExLink) 重写，使用 LSPosed 新一代 **libxposed API 102**，界面用 **Miuix** 重做。

- 包名：`io.github.sol01st.nobrowser`
- 版本：4.2.0（versionCode 30）
- minSdk 26 / targetSdk 36
- Xposed API：`io.github.libxposed:api:102.0.0`

## 功能

- **可选弹窗**：开启「每次询问」时点链接弹出选择框，可选用应用内浏览器还是手机浏览器；关闭后点链接直接交给手机浏览器，不再弹窗
- **实时生效**：改完开关不需要杀应用，下一次点链接就按新配置走（拦截前会检查配置文件时间戳）
- **作用域双向同步**：在 LSPosed 里勾选/取消作用域，模块首页会自动同步开关状态；在模块里开关应用也会写回 LSPosed 作用域
- **规则引擎**：Activity 支持 `*` `?` 通配，不区分大小写，同时匹配「发起跳转的 Activity」和「Intent 指向的目标 Activity」
- **取值方式**：`ExAuto`（自动在 data/extras/Bundle 里找第一个 http 链接）、`ExDat`（只读 Intent.data）、或指定 extras key
- **白名单**：按域名放行，命中白名单的链接保持应用内打开
- **导入 / 导出**：规则可导出为 JSON，也可以从文件恢复
- **主题**：跟随系统 / 浅色 / 深色

默认接管：QQ、微信、QQ邮箱、百度贴吧、钉钉、TIM。其他应用点右下角 `+` 添加。

## 安装

1. 从 [Releases](../../releases) 下载 APK 安装
2. 在 LSPosed 中启用模块，勾选需要接管的应用
3. **首次接管某个应用后，需要在 LSPosed 作用域里对该应用重新勾选一次**（LSPosed 对后写入作用域的应用不会即时注入）
4. 打开一次模块，授予 root 权限（写入作用域与配置文件需要）

## 已知限制

- **微博**：LSPosed 无法把模块注入微博进程（作用域勾选、重启都试过，日志里没有任何注入记录），所以微博用不了
- 首次接管的应用需要在 LSPosed 里重新勾选一次作用域才能注入
- 作用域写入和配置发布依赖 root（通过内置的 sqlite3 直接维护 LSPosed 数据库与 `/data/local/tmp/nxb_config.json`）

## 源码与反馈

源码：<https://github.com/SoL01St/exlindev>

问题反馈请到源码仓库提 issue。

## 致谢

- [xloger/ExLink](https://github.com/xloger/ExLink)：原始规则与思路
- [libxposed/api](https://github.com/libxposed/api)：现代 Xposed API
- [compose-miuix-ui/miuix](https://github.com/compose-miuix-ui/miuix)：Miuix Compose 组件

## License

MIT
