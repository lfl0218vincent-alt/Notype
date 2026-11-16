# Notype API 配置教程

适用 Notype 0.8.2，整理日期 2026-11-17。API 是在线服务，不是另一个需要安装的软件。你只需要一个可用的服务商账户和自己的 API Key；无需安装 SDK、Python、Node.js 或下载模型。

## 三个名称分别是什么

- **服务商**：提供语音识别和文字处理的公司，例如 OpenAI、DeepSeek、Groq。
- **服务地址**：App 请求发送到哪里。选预设服务商后自动填写；它不是密钥。
- **API Key**：你的账户访问凭据。去对应服务商官网创建，再由你本人粘贴到 App 的 Key 输入框。不要发给朋友、Codex 对话、邮件或 GitHub Issues。

服务商通常分别统计语音和文字用量。ChatGPT、DeepSeek 等聊天产品的登录状态，不等于 Notype 的 API 已配置；API 可用额度、订阅附带权益、收费和账户权限以服务商后台为准。模型与服务需要在你所在地区可用，不承诺免费额度或所有账户都能使用全部模型。

## 1 选择一套服务

默认情况下，语音识别和文字整理共用同一服务商与同一个 Key。下面列出这个版本内置的默认选项：

| 服务商 | 自动填写的服务地址 | 语音选项 | 默认文字模型 | 创建 Key |
| --- | --- | --- | --- | --- |
| OpenAI 官方 | `https://api.openai.com/v1` | GPT-Transcribe / `gpt-transcribe` | GPT-6.1 Sol / `gpt-6.1-sol` | [OpenAI 密钥页面](https://platform.openai.com/api-keys) |
| DeepSeek 官方 | `https://api.deepseek.com` | DeepSeek ASR，固定选项 | DeepSeek Flash / `deepseek-flash` | [DeepSeek 密钥页面](https://platform.deepseek.com/api_keys) |
| Groq | `https://api.groq.com/openai/v1` | Whisper Large V3 Turbo / `whisper-large-v3-turbo` | GPT OSS 20B / `openai/gpt-oss-20b` | [Groq 密钥页面](https://console.groq.com/keys) |

如果已有其中一家可用的 API 账户，优先用自己的那一家。没有账户时，选择你能正常访问和注册、费用可接受的服务商。先完成一套服务的配置，暂时不用打开“文字使用其他服务”。

## 2 注册并创建 Key

1. 打开 Notype“设置 → 高级：服务与模型”。
2. 在“服务商”下拉中选择你要使用的服务，点击 Key 旁的“获取 API Key”。也可以打开上表中的对应官方链接。
3. 在官网由你本人完成注册/登录和必要验证。进入 API keys 页面，选择创建新密钥；按钮可能称为“Create new secret key”“Create API key”或“创建 API Key”。
4. 可将密钥命名为“Notype”，方便以后识别与撤销。Key 所属项目/账户需要有对应语音和文字接口权限。
5. 按服务商当前要求检查 API 额度、计费设置或充值。付款与消费限制由你本人决定；不要让别人代填支付资料。
6. 创建后复制完整 Key。有的服务只显示一次完整值；遗失时应在官方后台重新创建，而不是寻找他人的 Key。

## 3 填入 Notype 并保存

1. 回到 Notype，确认选择的服务商与刚才创建 Key 的网站一致。
2. 在 **API Key** 输入框粘贴完整密钥，不加引号、不加 `Bearer` 前缀，也不要把服务网址填到这里。
3. 语音模型和文字模型先保留上表对应的默认选项。想换文字模型，可以从下拉菜单选择自己账户可用的模型。
4. 保持“文字使用其他服务”关闭，这样一套服务地址和 Key 就用于两个阶段。
5. 点击 **保存服务设置**。

输入框之后变空并显示“已保存”，是 App 隐藏密钥的正常表现，不是丢失。以后留空保存会保留当前服务已有 Key；填入新 Key 会替换。选择新服务商后也要点击保存；旧服务商的 Key 不能当作新服务商的 Key 使用。

“已保存”只证明本地保存成功，不代表账户余额、网络和模型权限都已验证。接下来按安装教程完成一次简短语音测试。

## 三家服务的补充说明

**OpenAI**：语音默认 GPT-Transcribe，文字默认 GPT-6.1 Sol。创建 Key 的入口位于 API 平台，不是 ChatGPT 对话框。以 API 平台显示的模型权限和额度为准。参考 [API 入门](https://developers.openai.com/api/docs/quickstart)、[语音识别](https://developers.openai.com/api/docs/guides/speech-to-text) 和 [GPT-6.1 Sol](https://developers.openai.com/api/docs/models/gpt-6.1-sol)。

**DeepSeek**：选择后语音固定使用 DeepSeek ASR，无需填写语音模型 ID；文字默认 Flash，也可选择账户可用的 Pro。Notype 会自动转换录音格式，并在约 119 秒结束录音以满足服务时长限制。不要把文字模型名当成语音模型名。参考 [官方 API 入门](https://api-docs.deepseek.com/) 和 [ASR 文档](https://api-docs.deepseek.com/guides/asr/)。

**Groq**：这是 GroqCloud，不是 Grok。选择 Groq 后使用它自己的 Key，默认语音为 Whisper Large V3 Turbo、文字为 GPT OSS 20B；账户可用时可选其他预设。参考 [语音文档](https://console.groq.com/docs/speech-to-text) 和 [支持模型](https://console.groq.com/docs/models)。

## 语音和文字想用不同服务

例如用 Groq 识别语音、DeepSeek 整理文字：

1. 上方“服务商”选 Groq，填写 Groq Key，语音模型选择 Whisper Large V3 Turbo。
2. 打开“文字使用其他服务”。
3. 在新出现的文字服务设置中选 DeepSeek 官方，填写 DeepSeek Key，文字模型选择 DeepSeek Flash。
4. 点击“保存服务设置”。

此时需要两家服务的 Key。不要向一个服务地址发送另一家服务商的密钥。普通用户使用共用模式即可。

## 自定义服务

只有在服务提供方给出了兼容接口文档、HTTPS 基础地址、模型 ID 和 Key 时才使用“自定义”。OpenAI 兼容语音一般需要 `/audio/transcriptions`，文字需要 `/chat/completions`；在地址栏填基础地址，不要把完整功能路径重复加进去。仅支持聊天网页或只有文字模型的服务，不能直接承担语音识别。自定义服务的“获取 API Key”按钮没有预设入口，请到对应官方后台办理。

## 错误排查

| 提示或现象 | 先检查 |
| --- | --- |
| 没有配置 Key | 是否在正确服务商下填写，并点击了“保存服务设置”。 |
| 401 或鉴权失败 | Key 是否完整、是否已撤销、是否属于当前服务商。不要把完整 Key 发给客服或 Codex。 |
| 403 或无权限 | 当前账户/项目是否可用该接口和模型，地区或组织策略是否有限制。 |
| 402、余额或额度不足 | 在服务商后台确认 API 余额和计费状态，由本人决定是否充值。 |
| 404 或模型不存在 | 基础地址和模型 ID 是否匹配，是否选择了账户实际支持的模型。 |
| 429 | 可能触发请求/用量限制，也可能是账户额度问题；按服务提示检查后台，稍后再试。 |
| 超时或连接失败 | 检查网络和服务状态；不要通过切换到不可信代理来提交你的 Key。 |
| 语音成功但文字整理失败 | 检查文字模型权限、独立文字服务的地址和 Key。 |

## 数据会去哪里

语音录音发送给所选语音服务，识别出的文字和词典用于所选文字服务。划词翻译发送所选文字，划词总结还可能包含同一会话已加载的附近内容。Key 保存在当前 Mac 钥匙串；录音临时文件在处理结束或取消后删除，历史文本按 Notype 设置保留。请使用没有私密信息的一句话完成第一次测试。
