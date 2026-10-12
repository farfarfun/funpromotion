# 更新日志

## [4.0.0] - 未发布

### 新增

- 增加 ChatGPT workspace 加入/接受邀请 userscript。
- 提供 K12 v1/v2 两种脚本版本。

### 修复

- k12-v2.js：移除明文登录凭证的复制、下载和批量导出功能，避免在浏览器端输出 `access_token`、`refresh_token`、`id_token` 等凭证。
- k12-v1.js：`DEFAULTS.workspace_ids` 默认值改为空，取消首次获取 AT 后自动发起 Request 的行为，改为仅提示用户手动点击。
- README：更正 session 行为说明，明确 v1 仅使用 `accessToken`，并移除已删除的凭证导出说明。

### 变更

- v1 保持手动填写 workspace ID 的使用方式；v2 提供批量处理界面。

### 废弃

- 无。
