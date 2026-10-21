# Google Antigravity Clash Ruleset

Google Antigravity & AI Developer Suite 专用的 Clash / Mihomo 规则集。

## 包含内容
- Google Antigravity 专有服务与灰度下发 (`antigravity.google`, `antigravity-unleash.goog`)
- Google Cloud Code / AI 编程协同接口 (`cloudcode-pa.googleapis.com`, `daily-cloudcode-pa.googleapis.com`)
- Vertex AI / Enterprise 核心推理通道 (`aiplatform.googleapis.com`)
- Google DeepMind 与 AI Studio (`deepmind.google`, `aistudio.google.com`)
- Gemini 核心模型推理接口 (`generativelanguage.googleapis.com`, `proactivebackend-pa.googleapis.com`)
- OAuth2 与相关配置服务

## 引用方式

### Clash Rule-Provider (CDN 加速)
```yaml
rule-providers:
  antigravity:
    type: http
    behavior: classical
    url: "https://testingcf.jsdelivr.net/gh/Floatingcloud01/clash-rules-antigravity@main/antigravity.yaml"
    path: ./ruleset/antigravity.yaml
    interval: 86400
```
