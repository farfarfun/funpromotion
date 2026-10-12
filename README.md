# funpromotion
运行在 `chatgpt.com` 上的浏览器脚本，用于在 ChatGPT workspace 中提交加入/接受邀请请求。

仓库包含两个独立脚本，安装方式不同：

- `codex/v20260705-linuxdo/k12-v1.js`：**Tampermonkey userscript**，手动填写 workspace ID 并发起加入申请/接受邀请，默认不自动发起任何请求。
- `codex/v20260705-linuxdo/k12-v2.js`：**书签小程序（Bookmarklet）**，不是 userscript，不能导入 Tampermonkey；提供批量上车/下车。

两个脚本都会从当前登录账号的 session 中读取 `accessToken`，仅用于向 ChatGPT workspace API 发起上车、接受邀请或下车请求；不会导出登录凭证。v1 只使用 `accessToken`，不会读取或导出 `refresh_token`、`id_token` 等其他凭证字段。

## 安装与使用：k12-v1.js（Tampermonkey userscript）

1. 在已登录 ChatGPT 的浏览器中安装 Tampermonkey（或兼容的 userscript 管理器）。
2. 新建脚本，复制 `codex/v20260705-linuxdo/k12-v1.js` 的全部内容并保存，也可以直接拖拽该文件导入 Tampermonkey。
3. 打开 [chatgpt.com](https://chatgpt.com/) 并保持登录子号，脚本会在右上角显示控制面板并自动读取当前账号 AT（不会自动发起请求）。
4. 在面板中填写母号 workspace ID（一行一个 UUID），点击「保存」。
5. 点击「Request」主动申请加入该 workspace，或点击「Accept」接受已有邀请；两者都需要手动点击才会执行。

## 安装与使用：k12-v2.js（Bookmarklet）

1. 打开 `codex/v20260705-linuxdo/k12-v2.js`，复制整行内容（以 `javascript:` 开头）。
2. 在浏览器书签栏新建一个书签，把网址（URL）字段粘贴为该行内容，名称任意。
3. 登录 ChatGPT 并打开 [chatgpt.com](https://chatgpt.com/) 页面，点击该书签即可弹出悬浮面板；再次点击书签会关闭面板。
4. 面板按钮说明：
   - **获取当前工作区 ID**：把当前所在 workspace 的 ID 填入输入框。
   - **上车**：必须填写目标 workspace ID；对输入框中的每个 ID 发起加入申请。
   - **下车**：从填写的 workspace 退出当前账号；对当前 workspace 执行下车或输入框留空直接下车都会二次确认，因为可能导致账号退出登录、使其它 workspace 的 access token 失效。
5. 批量处理（多个 workspace ID）时，每个 workspace 之间会有约 0.5～1 秒的请求间隔；workspace ID 需为合法 UUID 格式，否则会提示格式错误并中止。

## codex
[【K12 】gmail - 喂饭级教程](https://linux.do/t/topic/2518611)

[K12-gmail 空间ID 分享](https://linux.do/t/topic/2523396)

---

## 关于 farfarfun

[farfarfun](https://github.com/farfarfun) 是一个专注于实用工具库的开源组织，
涵盖云存储、数据处理、AI、多媒体与开发工具链等方向。

- 🏠 组织主页：<https://github.com/farfarfun>
- 📧 联系：farfarfun@qq.com

本项目基于 [MIT](LICENSE) 协议开源。
