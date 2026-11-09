# Rewind for X — Userscript 版

X（Twitter）首页时间线的"刚刚看过"抽屉：刷过、被顶掉的推文不再消失，随时回看。

这是一个非官方的 **Tampermonkey / Violentmonkey 油猴脚本移植版**，移植自 [yetone/rewind-for-x](https://github.com/yetone/rewind-for-x)（Chrome 扩展）。原扩展由 [yetone](https://github.com/yetone) 借助 Claude Opus 完成，代码干净利落，向原作者致敬。

> 本脚本与 X Corp. 无关，也不是 X 的官方产品。

## 安装

1. 浏览器安装 [Tampermonkey](https://www.tampermonkey.net/) 或 [Violentmonkey](https://violentmonkey.github.io/)（手机端：Firefox / Edge / Kiwi 等支持扩展的浏览器均可）；
2. 新建脚本，粘贴 `rewind-for-x.user.js` 的全部内容并保存；
3. 打开 [x.com](https://x.com) 首页刷推，右下角会出现悬浮按钮，点开即抽屉。

快捷键：`Alt+Shift+R` 开合抽屉（也可在脚本菜单里点"刚刚看过"）。

## 功能

- 自动记录你在 **/home 首页**滚过一半以上的推文：正文、引用、图片/视频封面链接、上下文；
- 抽屉按"会话"分组（间隔 10 分钟以上视为新会话），支持全文搜索；
- **筛选标签**：全部 / 图片 / 视频 / 引用 / 转帖，选择会被记住；
- 上限 3000 条，超出自动淘汰最旧记录；多标签页同时刷推时合并记录（以最早看见为准）；
- 深度适配 X 三套主题（浅色 / 暗蓝 / 纯黑），Shadow DOM 隔离，不污染页面样式；
- 手机端自动停靠在发推按钮上方，不遮挡任何原生控件。

## 隐私

所有数据仅存储在本机脚本管理器的存储中，脚本**不发出任何网络请求**（抽屉中的图片由浏览器直接从 X 的 CDN 加载，与正常刷推一致），不上传、不共享、无任何遥测。

## 与原扩展的差异

| | Chrome 扩展 | 本脚本 |
|---|---|---|
| 存储 | `chrome.storage.local` | `GM_setValue` + 跨标签页变更监听 |
| i18n | `chrome.i18n` | 内置中/英字典，按浏览器语言选择 |
| 入口 | 工具栏图标 / 快捷键 | 脚本菜单命令 / `Alt+Shift+R` / 悬浮按钮 |
| 手机端 | 不适用 | 适配（停靠发推按钮上方） |

其余逻辑（抽取、监听、UI）与上游保持同步，上游更新后本仓库尽快跟进移植。

## 许可

MIT License — 版权归上游作者 yetone（见 LICENSE），本移植版遵循同一许可，脚本头部保留版权与出处声明。
原项目：[yetone/rewind-for-x](https://github.com/yetone/rewind-for-x)。
