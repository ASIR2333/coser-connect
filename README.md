[README.md](https://github.com/user-attachments/files/32659748/README.md)
# coser-connect
Expo Stamp Rally — 漫展集邮：帮助 Coser 发现同场角色、一键发起集邮的微信小程序 + 纯本地可运行的 Web Demo（原生 HTML/CSS/JS，Mock + localStorage，无后端、双击即用）。
# 漫展集邮 · Web 交互 Demo

本项目是「漫展集邮」的 Web 交互 Demo。

Demo 使用原生 HTML / CSS / JavaScript 构建，
业务数据采用 Mock + localStorage 模拟。

为了保证项目可以零成本本地运行，
Demo 没有接入真实用户系统、数据库、
地图定位服务、图片服务器和后端 API。

核心产品流程：

漫展选择 → 角色发现 → 角色详情 → 发送集邮请求 → pending → accepted / rejected

原微信小程序源码保留在 `/miniprogram` 目录。

## 运行

双击 `web-demo/index.html`（或右键 → 浏览器打开），无需 npm / Node / 服务器，断网可运行。

## 说明

- 默认 Demo 用户：`我自己`，无微信登录 / OpenID。
- 地图为模拟漫展平面图（SVG），无真实定位与地图 SDK。
- 发布页图片走 `<input type="file">` 本地预览 + localStorage，不上传服务器。
- 社区内容仅为 Mock Demo 数据（广场页只读展示）。
- 主题 light / dark 保存在 localStorage，刷新保留；请求状态刷新保留。

## 迁移映射（小程序 → Web）

| 小程序 | Web Demo |
|---|---|
| pages/home/index.wxml+wxss+js | js/app.js renderHome + css |
| pages/role-detail | js/app.js renderDetail |
| pages/collect-record（请求记录） | js/app.js renderJipiao（底部「集邮」Tab） |
| pages/collect（广场） | js/app.js renderSquare（首页「逛广场」入口，Mock 只读） |
| pages/publish | js/app.js renderPublish |
| pages/message | js/app.js renderMessage |
| pages/mine | js/app.js renderMine |
| pages/exhibition-select | js/app.js renderExhibitions |
| pages/map（腾讯地图） | js/app.js renderMap（SVG 模拟平面图） |
| mock/role,exhibition,request,user,post | data/roles,exhibitions,requests,users,messages.js |
| utils/storage（wx.*） | js/storage.js（localStorage） |
| utils/util, theme, app.js 主题/登录 | js/utils.js, css/variables.css, js/state.js |
| components/role-card,request-card,status-tag,exhibition-card,empty-state,loading | js/components/components.js |

删除：微信登录/OpenID、wx.* API、GPS、腾讯地图、云开发/后端、WebSocket、真实社区发布/评论/点赞/举报/拉黑（详情页仅保留展示说明）。
