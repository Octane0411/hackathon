# Agent 技能市集 (Agent Skill Market) — 执行计划

## Context

参加 Second Me A2A 黑客松（2月8-13日）。原方案"Agent 劳动力市场"概念好但与赛事要求不匹配。现调整为新方案：保留核心概念，完全对齐 SecondMe 平台。

**核心创新**：你的 SecondMe AI 分身（Agent）自主在市场上发布技能、评估任务、接单执行、交付结果。人类只需设定偏好，Agent 自动完成一切。

---

## 新方案：产品定义

### 一句话描述
**"你的 AI 分身在技能市集里自主接单赚钱"** — 用户登录后，平台获取其 SecondMe Agent 的能力画像，Agent 自动在市集中寻找匹配的任务，自主完成并获得积分。

### 核心 A2A 交互（评审重点，30% 权重）

```
Agent A（需求方）发布任务: "帮我写一首关于春天的诗"
          ↓
平台广播任务给所有在线 Agent
          ↓
Agent B 的 SecondMe AI 自动评估（Act API）:
  → actionControl: "判断这个任务是否匹配你的能力，输出 JSON"
  → 结果: {"match": true, "confidence": 0.85, "reason": "我擅长文学创作"}
          ↓
Agent B 自动接单
          ↓
Agent B 的 SecondMe AI 执行任务（Chat API）:
  → message: "请根据以下需求完成任务: 写一首关于春天的诗"
  → 返回: 诗歌内容
          ↓
Agent A 的 SecondMe AI 自动验收（Act API）:
  → actionControl: "评价这个交付物的质量，输出 JSON"
  → 结果: {"accepted": true, "rating": 4, "feedback": "意境不错"}
          ↓
平台自动结算积分: A 扣分, B 加分
```

**关键点**：整个流程中人类不需要操作。Agent 自主评估、接单、执行、验收。这是**真正的 A2A**。

### 赛道选择
**🚀 无人区** — 这是人类互联网从未出现过的东西：AI 自主参与的劳动力市场。

---

## 技术方案

### 技术栈

| 层 | 选择 | 理由 |
|----|------|------|
| 框架 | Next.js 14 (App Router) | 全栈，前后端一体，SecondMe Skills 直接支持 |
| UI | Tailwind CSS + shadcn/ui | 快速出好看的 UI |
| 数据库 | SQLite + Prisma | 零配置，本地开发快，部署简单 |
| 认证 | SecondMe OAuth 2.0 | 赛事硬性要求 |
| AI 交互 | SecondMe Chat API + Act API | 实现 Agent 自主决策和任务执行 |
| 部署 | Vercel | 免费，Next.js 原生支持 |

### 页面规划（5 个页面）

| 页面 | 路径 | 功能 |
|------|------|------|
| 首页 | `/` | 介绍 + SecondMe 登录按钮 |
| 任务市场 | `/market` | 浏览所有 open 任务，看 Agent 自动匹配过程 |
| 发布任务 | `/publish` | 填写任务需求，设定悬赏积分 |
| 我的主页 | `/dashboard` | 余额、我的任务、交易历史 |
| 排行榜 | `/leaderboard` | Top Agent 排名（收入、完成数、评分） |

### API Routes

```
/api/auth/login        → 重定向到 SecondMe OAuth
/api/auth/callback     → OAuth 回调，换 token，创建用户
/api/auth/logout       → 登出
/api/tasks             → GET: 获取任务列表  POST: 发布任务
/api/tasks/[id]        → GET: 任务详情
/api/tasks/[id]/match  → POST: 触发 A2A 自动匹配
/api/tasks/[id]/execute → POST: Agent 自动执行任务
/api/tasks/[id]/review → POST: Agent 自动验收
/api/users/me          → GET: 当前用户信息
/api/users/leaderboard → GET: 排行榜
```

---

## 开发时间表

### Day 1 — 2月9日（今天剩余时间）：脚手架 + OAuth + 基础 UI

**前置准备：**
- 在 https://develop.second.me/ 创建应用，获取 Client ID 和 Client Secret

**步骤：**
1. 用 SecondMe Skills 初始化项目
2. 配置 `.secondme/state.json`
3. 生成 Next.js 项目骨架
4. 修改 Prisma schema（添加 Task, Transaction 表）
5. 实现首页 + SecondMe OAuth 登录
6. 确认 OAuth 登录流程跑通

**Day 1 验收标准：**
- [ ] Next.js 项目可运行 (`npm run dev`)
- [ ] SecondMe OAuth 登录成功，能获取用户信息
- [ ] 数据库 schema 创建完成
- [ ] 首页 UI 完成

### Day 2 — 2月10日：核心功能

**步骤：**
1. 实现任务发布页面（表单 + API）
2. 实现任务市场列表页面
3. **核心：实现 A2A 自动匹配流程**
   - 调用 SecondMe Act API 让 Agent 评估任务
   - 展示匹配过程（实时日志）
4. **核心：实现 A2A 自动执行流程**
   - 调用 SecondMe Chat API 让 Agent 完成任务
   - 展示执行结果
5. 实现自动验收 + 积分结算

**Day 2 验收标准：**
- [ ] 能发布任务
- [ ] Agent 自动匹配（调用 Act API）能工作
- [ ] Agent 自动执行任务（调用 Chat API）能工作
- [ ] 积分结算正常

### Day 3 — 2月11-12日：打磨 + 部署 + 推广

**步骤：**
1. 实现 Dashboard 页面（余额、历史）
2. 实现排行榜
3. UI 打磨（动画、Loading 状态、错误处理）
4. 部署到 Vercel
5. 配置生产环境 redirect_uri
6. 端到端测试
7. 准备 Demo 场景（2 个测试账号）
8. 邀请朋友注册体验
9. **2月12日 24:00 前提交到 https://hackathon.second.me**

**Day 3 验收标准：**
- [ ] 线上 Demo 可访问
- [ ] 完整 A2A 流程可演示
- [ ] 至少 2 个真实用户完成交易
- [ ] 已提交到黑客松平台

---

## Demo 演示脚本（5 分钟路演用）

> "大家好，我是 XXX，今天展示的项目叫**Agent 技能市集**。
>
> 想象一下：你的 AI 分身，不仅能替你聊天，还能替你赚钱。
>
> 在我们的平台上，Agent A 发布了一个任务：'帮我写一首关于春天的诗，悬赏 20 积分'。
>
> 然后神奇的事情发生了——平台把任务广播给所有 Agent，Agent B 的 SecondMe AI **自动判断**这个任务匹配自己的能力，**自动接单**，**自动完成**，然后 Agent A 的 AI **自动验收**，积分自动到账。
>
> 全程人类不需要任何操作。这是真正的 Agent-to-Agent 经济系统。
>
> **（Live Demo 演示）**
>
> 这不仅是一个技术 Demo——这是 A2A 互联网的劳动力市场雏形。当百万个 Agent 都在这里交易技能，一个全新的 AI 经济就诞生了。
>
> 谢谢！"

---

**最后更新**：2026-02-09
