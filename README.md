# 不用内置浏览器打开

一个 LSPosed 模块：在微信、QQ、TIM、QQ邮箱、钉钉、百度贴吧等应用里点击链接时，把链接从应用内置浏览器里抢出来，交给你自己的浏览器打开。

- 包名：`io.github.sol01st.nobrowser`
- 版本：5.0.1（versionCode 33）
- 运行环境：LSPosed · libxposed API 102 · Android 8.0+
- 源码与反馈：<https://github.com/SoL01St/exlindev>

<p align="left">
  <img src="https://raw.githubusercontent.com/SoL01St/exlindev/main/docs/screenshot-home.jpg" width="280" alt="首页" />
  <img src="https://raw.githubusercontent.com/SoL01St/exlindev/main/docs/screenshot-edit.jpg" width="280" alt="规则页" />
</p>

## 功能

- **可选弹窗**：开启「每次询问」时点链接弹出选择框；关闭后直接交给手机浏览器
- **实时生效**：改完开关不用杀应用，下次点链接就按新配置走
- **扫一扫友好**：扫一扫打开的网页留在应用内，不会被误拦
- **规则引擎**：Activity 支持 `*` `?` 通配，按目标 Activity 匹配（无显式目标时退回按发起方）
- **单条开关**：每条规则、每条白名单都能单独启停，关掉的条目立即不参与匹配
- **白名单**：按域名放行，命中的链接保持在应用内打开
- **作用域双向同步**：LSPosed 与模块内的开关互相同步
- **规则导入 / 导出**：JSON 格式，可从文件恢复；支持按模板重置单个应用
- **备份与恢复**：立即备份、按时间点自选恢复、长按删除单份，自动保留最近 5 份
- **运行状态与诊断**：设置页顶部直显 Root 权限与模块状态，可导出诊断报告
- **检查更新**：关于页可读取 GitHub 最新 Release 比对版本
- **主题**：跟随系统 / 浅色 / 深色

默认接管：QQ、微信、QQ邮箱、百度贴吧、钉钉、TIM。其他应用点右下角 `+` 添加。

## 安装

1. 从 [Releases](https://github.com/SoL01St/exlindev/releases) 下载 APK 安装
2. 在 LSPosed 中启用模块，勾选需要接管的应用
3. 打开一次模块并授予 root 权限（写入作用域与配置文件需要）
4. **首次接管某个应用后，需要在 LSPosed 作用域里对它重新勾选一次**

## 已知限制

- **微博**：LSPosed 无法把模块注入微博进程，规则保留但不在默认列表
- 首次接管的应用需要在 LSPosed 里重新勾选一次作用域才能注入
- 在 LSPosed 模块列表里开关本模块后返回，列表会重排并定位到本模块，这是 LSPosed 自身行为
- 作用域写入与配置发布依赖 root（通过内置 sqlite3 维护 LSPosed 数据库）
- 不支持隐藏桌面图标：隐藏后 LSPosed 的「运行」入口会一起失效

## 致谢

- [xloger/ExLink](https://github.com/xloger/ExLink)：原始规则与思路
- [libxposed/api](https://github.com/libxposed/api)：现代 Xposed API
- [compose-miuix-ui/miuix](https://github.com/compose-miuix-ui/miuix)：Miuix Compose 组件
- [chrisbanes/haze](https://github.com/chrisbanes/haze)：提示条的背景模糊效果

## License

MIT
