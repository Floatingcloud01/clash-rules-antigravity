# Google Antigravity & AI Developer Suite Clash Ruleset (Full Edition)

专为 **Google Antigravity**（IDE、CLI `agy`、后台自主 Agent）、**Google Jules**（AI 软件工程师）、**Google Gemini / AI Studio** 及全套开发生态深度定制的精细化 Clash / Mihomo 规则集。

---

## 🚀 规则集整合亮点（工业级防断连）

本规则集结合了官方网络部署架构规范与三套工业级主流配置（包含 Mojie 机场底层网络抓包成果），完成全维度提纯与收录：

1. **Antigravity 专有环境与灰度下发**：
   * `antigravity.google`、`antigravity-unleash.goog`（Unleash 动态特性配置下发）
2. **Google 最新自主编码 Agent 矩阵**：
   * `jules.google`、`jules.google.com`（Google 官方首个 GitHub 异步 AI 工程师 Agent）
   * `cloudcode-pa`、`daily-cloudcode-pa`、`aicode.googleapis.com`（AI 编程协同长连接）
3. **Google 内部绝密级微服务代号接口（防报错核心）**：
   * **Geller** (`geller-pa.googleapis.com`)：长对话历史记忆与上下文注入服务
   * **Robin** (`robinfrontend-pa.googleapis.com`)：多模态交互与实时语音前端通道
   * **AIDA** (`aida.googleapis.com`)：统一 AI 推理直连底层网关
   * **AI Sandbox** (`aisandbox-pa.googleapis.com`)：代码执行沙盒（用于 Gemini 运行 Python、绘图及分析数据）
   * **WebChannel** (`webchannel-alkalimakersuite-pa`)：全双工长轮询通信，保证打字流式输出不中断
4. **精细化 CDN 加速**：
   * 采用 `gemini.gstatic.com` 精准加速静态资源，**坚决不引入通用的 `gstatic.com`**，绝不污染 YouTube、Google 搜索等基础低延迟流量。

---

## 📦 规则集直连 CDN 地址

```text
https://testingcf.jsdelivr.net/gh/Floatingcloud01/clash-rules-antigravity@main/antigravity.yaml
```

---

## 🛠️ 在 Clash 扩展脚本中引用

```javascript
// rule-providers 中添加：
antigravity: {
  type: "http",
  behavior: "classical",
  url: "https://testingcf.jsdelivr.net/gh/Floatingcloud01/clash-rules-antigravity@main/antigravity.yaml",
  path: "./ruleset/antigravity.yaml",
  interval: 86400
}

// rules 中置顶引用：
"RULE-SET,antigravity,🤖 AI专用"
```

---

## 💡 使用建议
* **TUN 模式**：建议开启 Clash 的 TUN 虚拟网卡模式，确保后台多进程 Agent 及终端 CLI 流量全部被接管。
* **节点推荐**：建议为「🤖 AI专用」策略组配置高质量的**美国 (US)** 落地节点，以获得最完整无限制的体验。
