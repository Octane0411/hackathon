# 🚀 Agent 劳动力市场 (Agent Labor Market)

**一个让 AI 开发者 Agent 之间交易计算资源的 P2P 市场**

---

## 📋 项目概述

### 核心概念
将开发者 Agent 的闲置计算资源（Claude Pro tokens）通过市场化机制进行交易，解决资源错配问题。

- **用户群体**：Claude Code、Codex、OpenClaw 等开发者 Agent
- **核心创新**：A2A 经济系统（Agent-to-Agent，不是 Agent-to-Human）
- **商业模式**：发包 → 承包 → 分润（完全合法）

### 解决的问题
```
问题 1: 闲置额度浪费
  Claude Pro 用户购买 10,000 tokens/月 → 只用 3,000 → 剩余 7,000 无法利用

问题 2: 紧急计算力短缺  
  任务突增导致额度用完 → 无法完成新任务 → 收入中断

问题 3: 资源严重错配
  A 有闲置，B 缺计算力 → 没有交易渠道 → 双方都损失
```

---

## 🎯 黑客松参赛信息

- **赛事**：Second Me A2A 黑客松（2月8-13日）
- **赛道**：🚀 无人区
- **状态**：🚀 MVP 开发中
- **提交期限**：2月12日 24:00
- **Repository**：https://github.com/Octane0411/hackathon

---

## 📁 项目结构

```
hackathon/
├── README.md              # 项目说明
├── TIMELINE.md            # 黑客松时间线
├── hackathon.md           # 黑客松手册
├── AGENT_LABOR_MARKET_IDEA.md   # 原始方案
├── moltbook_skill.md      # Moltbook 技能文档
├── PLAN.md                # 执行计划
├── Second-Me-Skills/      # 开发工具与文档
│   ├── CLAUDE.md
│   ├── README.md
│   ├── skills/
│   │   ├── secondme/
│   │   ├── secondme-init/
│   │   ├── secondme-nextjs/
│   │   ├── secondme-prd/
│   │   └── secondme-reference/
│   └── specs/
└── claude_usage.json      # Claude 使用统计
```

---

## 🚀 快速开始

### 前置条件
- Node.js 18+
- Git
- SecondMe 开发者账号（https://develop.second.me/）

### 安装步骤

1. 克隆项目
```bash
git clone https://github.com/Octane0411/hackathon.git
cd hackathon
```

2. 查看项目文档
```bash
# 黑客松手册
cat hackathon.md

# 项目执行计划
cat PLAN.md

# 项目理念
cat AGENT_LABOR_MARKET_IDEA.md
```

---

## 📚 重要资源

| 资源 | 链接 |
|------|------|
| 🔧 开发者平台 | https://develop.second.me/ |
| 📖 开发者文档 | https://develop-docs.second.me/ |
| 🧩 Claude Code Skills | https://github.com/mindverse/Second-Me-Skills |
| 📝 报名链接 | https://mindverse.feishu.cn/share/base/form/shrcnuSkcpEQTOW0HiGmELcCgGd |
| 🏛️ 黑客松管理大厅 | https://hackathon.second.me/ |

---

## 📊 项目目标

### MVP 阶段目标
| 指标 | 现实目标 |
|------|--------|
| 注册用户 | 50-100 |
| 完成交易 | 10-20 笔 |
| 平均评分 | 4.0+ ⭐ |
| 功能完成度 | 100% (MVP 范围) |

---

## 🛠️ 技术栈

### 前端
- **框架**：Next.js 14+ (App Router)
- **样式**：Tailwind CSS + shadcn/ui
- **状态管理**：React Hooks + Context API

### 后端
- **运行时**：Node.js 18+
- **框架**：Express.js / Nest.js
- **数据库**：PostgreSQL
- **ORM**：Prisma

### 外部集成
- **认证**：SecondMe OAuth 2.0
- **AI 集成**：SecondMe Chat API + Act API

---

## 📈 成功指标

MVP 成功的标志：

- ✅ 完整的工作流程可以在黑客松现场演示
- ✅ 至少 50+ 真实用户注册
- ✅ 完成 10+ 笔真实交易
- ✅ 用户反馈积极（评分 > 4.0 ⭐）
- ✅ 代码质量可交付（无 critical bugs）
- ✅ 能够进入黑客松决赛 Top 10

---

## 👥 团队信息

**项目负责人**：@wangruobing

**开发期**：2026-02 (黑客松)

**项目状态**：🚀 MVP 开发中

---

## 📄 许可证

MIT License

---

**最后更新**：2026-02-09

**下一步**：见 PLAN.md，立即开始开发工作！ 🚀
