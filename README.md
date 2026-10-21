# Google Antigravity & AI Developer Suite Clash Ruleset

专为 **Google Antigravity**（IDE、CLI `agy`、后台 Agent）及 **Google Gemini / AI Studio** 深度定制的精细化 Clash / Mihomo 规则集。

---

## 💡 为什么需要这个专用规则集？（与通用 Google 规则的关系）

很多订阅自带的规则集中已经包含了通用的 `Google` 规则（收录了 `googleapis.com`、`gstatic.com`、`googleusercontent.com` 等全量域名）。

**那为什么不直接使用通用的 Google 规则，或者为什么本规则集不包含上述大域名？**

1. **解决地区限制冲突（核心目的）**：
   * **日常 Google 服务（YouTube、Google 搜索、Gmail）**：在香港 (HK)、台湾 (TW) 等低延迟节点体验最好，秒开 4K 视频。
   * **Antigravity / Gemini 服务**：Google 对 AI 服务有严格的地域风控，**香港节点通常直接提示“不支持该国家/地区”**，必须精准送往**美国 (US) 或特定支持节点**。
2. **避免“过度代理”，保护日常网络体验**：
   * Clash 的规则匹配逻辑是**自上而下匹配**，置顶的规则优先拦截。
   * 如果在 AI 专用规则里写了宽泛的 `DOMAIN-SUFFIX,googleapis.com` 或 `gstatic.com`，会导致你看 YouTube 视频流、网页字体、Chrome 同步等全部公共流量都被**强行绑架到速度较慢的 AI 节点**。
3. **本规则集的设计哲学——精准剥离**：
   * **只精准提取** Antigravity 和 Gemini 专属的模型推理接口、动态灰度端点（如 `antigravity-unleash.goog`）和 Cloud Code 协同管道；
   * 确保日常 YouTube / 搜索继续顺畅滑落到下方的通用 Google 规则（走快速香港节点），唯独 Antigravity / Gemini 精准命中专用组（走美国节点）。

---

## 📦 规则集直连 CDN 地址

```text
https://testingcf.jsdelivr.net/gh/Floatingcloud01/clash-rules-antigravity@main/antigravity.yaml
```

---

## 🛠️ 在 Clash 中引用示例

### 1. 添加到 `rule-providers`
```yaml
rule-providers:
  antigravity:
    type: http
    behavior: classical
    url: "https://testingcf.jsdelivr.net/gh/Floatingcloud01/clash-rules-antigravity@main/antigravity.yaml"
    path: ./ruleset/antigravity.yaml
    interval: 86400
```

### 2. 添加到 `rules`（建议置顶）
```yaml
rules:
  - RULE-SET,antigravity,🤖 AI专用
  # 放在你的通用 Google 规则上方
```

---

## 📌 使用建议
* **建议开启 TUN 模式**：Antigravity 调用的后台多进程 Agent 及 CLI 命令可能不遵循系统 HTTP 代理，开启 TUN 虚拟网卡接管可保证 100% 规则分流生效。
* **策略组节点推荐**：建议为「🤖 AI专用」策略组绑定高质量**美国 (US)** 节点。
