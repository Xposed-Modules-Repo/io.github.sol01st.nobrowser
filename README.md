# 不用内置浏览器打开

一个 LSPosed 模块：在微信、QQ、TIM、QQ邮箱、钉钉、百度贴吧、闲鱼里点击链接时，把链接从应用内置浏览器里抢出来，交给你自己的浏览器打开。

- 包名：`io.github.sol01st.nobrowser`
- 版本：5.0.2（versionCode 34）
- 运行环境：LSPosed · libxposed API 102 · Android 8.0+
- 源码与反馈：<https://github.com/SoL01St/exlindev>

<p align="left">
  <img src="https://raw.githubusercontent.com/SoL01St/exlindev/main/docs/screenshot-home.jpg" width="280" alt="首页" />
</p>

**默认接管：QQ、微信、QQ邮箱、百度贴吧、钉钉、TIM、闲鱼。其他应用点右下角 `+` 添加，需自行添加规则。**

## 功能

- **入口白名单**：只拦截已登记的发起方点出的链接，扫码、钱包、服务页等默认放行
- **可选弹窗**：每次询问，或直接交给手机浏览器
- **外链中转解包**：闲鱼、QQ 邮箱、钉钉自动还原真实地址
- **模块日志**：判定结果与原因，可复制、导出
- **规则引擎**：Activity 通配、单条启停、白名单 `=host`
- **实时生效**、作用域双向同步
- **备份恢复**、JSON 导入导出
- **界面**：折叠顶栏、悬浮底栏、实时毛玻璃，主题跟随系统

## 安装

1. 从 [Releases](https://github.com/SoL01St/exlindev/releases) 下载 APK 安装
2. 在 LSPosed 中启用模块，勾选需要接管的应用
3. 打开一次模块并授予 root 权限
4. 首次接管某个应用后，需要在 LSPosed 作用域里对它重新勾选一次

## 致谢

- 拦截规则与整体思路：[xloger/ExLink](https://github.com/xloger/ExLink)
- 模块框架：[libxposed/api](https://github.com/libxposed/api)
- 界面组件：[compose-miuix-ui/miuix](https://github.com/compose-miuix-ui/miuix)

## License

MIT
