# Open WebUI (Custom Edition)

<div align="center">
  <img src="./banner.png" alt="Open WebUI Banner" width="100%" />

  <br/>

  <img src="https://img.shields.io/badge/Version-v0.7.3--5-orange?style=for-the-badge&logo=git" alt="Version"/>
  <img src="https://img.shields.io/badge/Arch-x86__64%20%7C%20ARM64-blueviolet?style=for-the-badge&logo=docker" alt="Arch Badge"/>
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" alt="License"/>

<br/><br/>

  <h3>🚀 运营增强 · 💰 精细计费 · 🌏 深度汉化</h3>
  <p>基于 Open WebUI 构建，提供更强的模型集成、精细的计费系统及流畅的中文体验。</p>
</div>

---

## 📖 简介

本项目是 Open WebUI 的深度定制版本，旨在提供更完善的运营能力和更佳的本地化体验。除了继承上游的所有功能外，我们特别强化了计费控制、模型原生特性集成以及多架构部署支持。

| 核心亮点                                | 解决方案                                                                                   |
| :-------------------------------------- | :----------------------------------------------------------------------------------------- |
| **需要计费与流量控制？**                | ✅ **完善的积分计费系统**：支持按次或按 Token 计费，支持输入、输出及推理 Token 差别定价。  |
| **积分发放不方便？**                    | ✅ **兑换码功能**：内置兑换码生成与领取系统，支持一次性或多次领取的兑换码发放。            |
| **想用 OpenAI 新版 Responses API？**    | ✅ **首发支持**：完整兼容 `/v1/responses`，流式实时展示推理思考过程（Reasoning Content）。 |
| **Gemini 丢失原生特性？**               | ✅ **原生直连**：基于官方 SDK 开发，支持 `thinking_budget`、原生联网搜索及工具调用。       |
| **设备是树莓派、M1/M2 或 ARM 服务器？** | ✅ **多架构支持**：配套优化的 ARM64 镜像，拒绝 `exec format error`。                       |
| **觉得原版界面汉化不彻底？**            | ✅ **深度汉化**：全量人工校对，纠正生硬术语，提供专业友好的报错提示。                      |
| **代码高亮不好看？**                    | ✅ **专业字体 + 高亮配色**：内置 JetBrains Mono / Fira Code，适配 VS Code Light 风格。     |

---

## ✨ 核心特性

### 💰 精细化积分计费系统 (New!)

专为运营设计的计费闭环，让模型成本精确可控。

- **灵活计费模式**：支持全局或针对特定模型设置“按次”或“按 Token”计费。
- **分项定价**：可独立设置 **输入 Token**、**输出 Token** 及 **推理 Token** 的费率。
- **实时成本预览**：在对话窗口实时显示当前对话的 Token 消耗及折算金额。
- **兑换码系统**：管理员可生成指定积分额度的兑换码，支持设置有效期和使用限制。
- **流水追溯**：完整的积分变动历史记录，透明直观。

### 🧠 模型能力深度集成

- **OpenAI Responses API**
  - 实时流式展示 o1、o3 等推理模型的 Thinking Process。
  - 完美适配新版推理接口，让模型的“思考过程”可视化。
- **Google Gemini 原生 SDK**
  - 完美支持 `thinking_budget` 参数。
  - 支持原生 Google Search 联网搜索，无需额外插件。
- **推理强度控制 (Reasoning Effort)**
  - 为支持推理的模型提供 Low / Medium / High 预设，灵活平衡性能与成本。

### 🎨 交互与 UI/UX 优化

- **对话分支 (Branch Chat)**：支持从任意历史节点开启新分支，平行对比不同模型的回答。
- **可视化上下文控制**：支持插入 Context Break 物理隔断，图形化管理上下文长度。
- **智能 Logo 匹配**：内置 20+ LLM 提供商图标，算法自动为 GPT / Claude / Gemini / Qwen 配色。

---

## 🚀 快速开始

### 🐳 Docker 部署 (推荐)

```bash
docker run -d -p 3000:8080 \
  --add-host=host.docker.internal:host-gateway \
  -v open-webui:/app/backend/data \
  --name open-webui \
  --restart always \
  open-webui:latest
```

- **ARM64 设备**（如 M1/M2 Mac, 树莓派）：请确保使用适配 ARM64 的镜像标签。
- **持久化**：数据默认保存在 `/app/backend/data` 映射的卷中。

### 🛠️ 推荐配置流程

1.  **初始化**：设置首个管理员账号。
2.  **计费配置**：进入 **管理面板 -> 计费设置**，设置默认积分及模型费率。
3.  **生成兑换码**：在 **积分管理** 页面生成兑换码并分发给用户。
4.  **模型连接**：在 **设置 -> 外部连接** 中填入 API Key，开启 `Use Responses API` 体验流式推理。

---

## 📊 与官方版本对比

| 特性                     | 官方原版 (Upstream) |         本定制版 (Custom)         |
| :----------------------- | :-----------------: | :-------------------------------: |
| **积分计费系统**         |        ❌ 无        |     ✅ **完整计费 + 兑换码**      |
| **OpenAI Responses API** |        基础         |      ✅ **深度支持流式思考**      |
| **Gemini 深度集成**      |        基础         | ✅ **原生 SDK + Thinking Budget** |
| **对话分支管理**         |        ❌ 无        |       ✅ **多分支对话切换**       |
| **本地化汉化**           |       社区版        |   ✅ **精修版 (纠正生硬术语)**    |
| **ARM 设备支持**         |        基础         |        ✅ **原生优化构建**        |

---

## 📝 最近更新

- 🌐 **原生网页搜索**：支持 Gemini 原生 Google 搜索。
- 🔄 **智能降级**：Function Calling 失败时自动尝试降级兼容模式。
- 🎯 **计费逻辑优化**：增加对 DeepSeek 等模型推理 Token 的计费支持。
- 🎨 **界面重构**：设置页面改为卡片式布局，视觉更清爽。

---

## 🙌 声明

本项目基于 [Open WebUI](https://github.com/open-webui/open-webui) 进行二次开发，感谢原作者及社区。

- **许可证**：遵循 MIT License 协议。
- **同步策略**：我们定期合并上游特性，确保安全与功能同步。

<br/>

<p align="center">
  <sub>专注于更强的运营能力与更优的交互体验</sub>
</p>
