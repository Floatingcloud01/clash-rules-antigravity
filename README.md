# Clash Ruleset for Google Antigravity & AI Services

A tailored Clash / Mihomo routing ruleset for Google Antigravity, Google Jules, Gemini, and developer AI platforms.

专门针对 Google Antigravity、Google Jules、Gemini 及开发者 AI 服务的 Clash / Mihomo 分流规则集。

---

## 📌 Included Services / 包含服务

- **Google Antigravity**: `antigravity.google`, `antigravity-unleash.goog`
- **Google Jules** (Coding Agent): `jules.google`, `jules.google.com`
- **Cloud Code & Developer APIs**: `cloudcode-pa.googleapis.com`, `daily-cloudcode-pa.googleapis.com`, `aicode.googleapis.com`, `aiplatform.googleapis.com`
- **Google Gemini & AI Studio**: `gemini.google.com`, `aistudio.google.com`, `generativelanguage.googleapis.com`, `proactivebackend-pa.googleapis.com`, `alkalimakersuite-pa.clients6.google.com`
- **Google DeepMind & Labs**: `deepmind.google`, `deepmind.com`, `labs.google`, `flow.google`
- **NotebookLM**: `notebooklm.google`, `notebook.google`
- **Backend Support Endpoints**: Endpoints for context memory (`geller-pa`), voice frontend (`robinfrontend-pa`), and execution sandbox (`aisandbox-pa`).

---

## 💡 Design Notes / 设计说明

**Why not include generic domains like `googleapis.com` or `gstatic.com`?**  
**为什么不直接包含 `googleapis.com` 或 `gstatic.com` 等大域名？**

- **Preventing Over-proxying (避免过度代理)**:  
  `googleapis.com` and `gstatic.com` carry public traffic for YouTube, Google Search, and Chrome sync. Routing them entirely into AI proxies would degrade everyday streaming and search latency.
- **Accurate Routing (精准分流)**:  
  This ruleset isolates only AI-related endpoints, allowing standard Google services to use low-latency nodes (e.g., Hong Kong, Singapore) while AI traffic routes to supported regions (e.g., United States).

---

## 🚀 Quick Start / 快速配置

### 1. jsDelivr CDN URL / 规则集地址

```text
https://testingcf.jsdelivr.net/gh/Floatingcloud01/clash-rules-antigravity@main/antigravity.yaml
```

### 2. Clash Configuration Example / 配置示例

```yaml
rule-providers:
  antigravity:
    type: http
    behavior: classical
    url: "https://testingcf.jsdelivr.net/gh/Floatingcloud01/clash-rules-antigravity@main/antigravity.yaml"
    path: ./ruleset/antigravity.yaml
    interval: 86400

rules:
  # Place above generic Google / final match rules
  - RULE-SET,antigravity,YOUR_AI_PROXY_GROUP
```

---

## ⚙️ Recommendations / 使用建议

- **TUN Mode**: Recommended for developers using CLI tools (`agy`) or background processes that do not follow system HTTP proxy settings.
- **Node Selection**: Route this ruleset to proxy nodes in supported regions (e.g., United States) to avoid regional restrictions.
