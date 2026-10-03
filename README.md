# funpromotion
运行在 `chatgpt.com` 上的浏览器脚本，用于在 ChatGPT workspace 中提交加入/接受邀请请求，以及（v2）导出登录凭证配置。

仓库包含两个独立脚本，安装方式不同：

- `codex/v20260705-linuxdo/k12-v1.js`：**Tampermonkey userscript**，手动填写 workspace ID 并发起加入申请/接受邀请，默认不自动发起任何请求。
- `codex/v20260705-linuxdo/k12-v2.js`：**书签小程序（Bookmarklet）**，不是 userscript，不能导入 Tampermonkey；提供批量上车/下车，以及导出 Codex auth.json / CPA JSON / sub2api bundle 三种格式的登录凭证。

⚠️ 两个脚本都会读取当前登录账号的 session（access_token / refresh_token / id_token 等），v2 还支持将这些凭证导出为明文文件或剪贴板文本。**导出的文件或文本包含明文登录凭证，任何拿到它的人都可以直接登录或调用你的账号**，请勿在不受信任的环境中使用，妥善保管导出结果，不要分享给他人。脚本执行前会弹出风险确认提示，务必仔细阅读后再继续。

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
   - **上车**：对输入框中的每个 workspace ID 发起加入申请（留空则对当前 workspace 操作）。
   - **下车**：从填写的 workspace 退出当前账号；对当前 workspace 执行下车或输入框留空直接下车都会二次确认，因为可能导致账号退出登录、使其它 workspace 的 token 失效。
   - **复制 / 下载**：按下拉框选择的格式（Codex auth.json / CPA JSON / sub2api bundle）生成凭证并复制到剪贴板或下载为文件；执行前会弹窗提示凭证为明文、需确认风险。复制仅支持单个 workspace ID，批量请使用下载。
   - **一键上车并导出凭证**：对输入框中的每个 workspace ID 依次执行上车并导出对应凭证，同样会先弹出风险确认提示。
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
