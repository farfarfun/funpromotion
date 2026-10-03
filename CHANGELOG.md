# 更新日志

## [4.0.0] - 未发布

### 新增

- 增加 ChatGPT workspace 加入/接受邀请 userscript。
- 提供 K12 v1/v2 两种脚本版本。

### 修复

- k12-v2.js：复制/下载凭证与「一键上车并导出凭证」执行前新增明文凭证风险确认弹窗，未确认不再执行导出。
- k12-v1.js：`DEFAULTS.workspace_ids` 默认值改为空，取消首次获取 AT 后自动发起 Request 的行为，改为仅提示用户手动点击。
- README 补充 v1（Tampermonkey userscript）与 v2（Bookmarklet）各自的安装步骤、按钮行为、凭证导出风险说明。

### 变更

- v1 保持手动填写 workspace ID 的使用方式；v2 提供批量处理界面。

### 废弃

- 无。
