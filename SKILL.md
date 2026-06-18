---
name: marketing
description:
  市场营销技能套件：SEO优化、品牌审查、广告合规、活动策划、社媒趋势、竞品跟踪、营销分析、文案撰写。
  SEO优化: SEO优化, SEO, 关键词优化, 搜索排名; 品牌审查: 品牌审查, 品牌调性, brand review, 品牌一致性; 广告合规: 广告合规, 极限词, 广告法; 活动策划: 活动策划, 营销活动, campaign, 促销方案; 社媒趋势: 社媒趋势, 热点追踪, 社交监听; 竞品跟踪: 竞品跟踪, 竞品监控, 竞品动态; 营销分析: 营销分析, ROI, 获客成本; 文案撰写: 文案撰写, 文案, copywriting, 营销文案。
version: "1.0.1"
author: "智慧半岛"
---

# marketing -- 市场营销综合技能

本技能是一个综合技能套件，包含多个子技能。接到用户请求后，按以下流程执行。

## 执行流程

### Step 1: 意图识别与路由匹配

分析用户输入，与下方路由表逐一比对。匹配规则：
- 用户输入中包含路由表中「子技能」列的关键词 → 匹配该子技能
- 用户输入中包含路由表中「功能说明」列中提到的场景 → 匹配该子技能
- 多个子技能同时匹配时，选择匹配度最高的
- 无法唯一确定时，向用户确认意图

### Step 2: 加载子技能模板

匹配到子技能后，根据子技能索引表找到对应的文件路径，**必须**使用 `read_text` 工具读取 `references/` 目录下的完整执行模板。

### Step 3: 按模板执行

严格按照加载的模板逐步执行。模板中定义了：
- 输入要求（用户需要提供什么）
- 执行步骤（每一步做什么、如何判断）
- 输出格式（最终产出的结构和规范）
- 质量标准（产出必须满足的底线）

### Step 4: 输出结果

按模板规定的格式输出结果。如果模板要求生成文件，写入后声明产出物。

## 约束规则

1. **必须先读模板再执行**：匹配到子技能后，严禁凭记忆或猜测执行，必须先读取对应的 references 文件
2. **严格遵循模板**：不得跳过步骤、不得省略检查项、不得自行简化流程
3. **输入不足时主动索取**：模板中标注「必填」的输入项缺失时，向用户索取
4. **质量底线不妥协**：模板中的质量标准必须逐条满足

## 路由表

| 子技能 | 功能说明 |
|--------|----------|
| SEO内容优化 | 输入网站URL或文章内容，进行全面SEO诊断（技术SEO + 页面SEO +... |
| 品牌调性审查 | 输入品牌指南和待审查内容，逐段审查内容与品牌调性的一致性... |
| 广告合规检查 | 输入宣传文案，对照《广告法》及行业特规逐句扫描极限词和违规表述，按风险等级分类... |
| 活动策划 | 输入活动目标和预算，输出完整可落地的活动方案... |
| 社媒热点追踪 | 获取当日全网热点话题，评估借势安全性和品牌匹配度... |
| 竞品追踪 | 输入竞品名称，追踪竞品最新动态，输出功能对比矩阵、品牌定位分析、SWOT分析... |
| 营销效果分析 | 输入各渠道投放数据，输出完整营销效果分析报告... |
| 营销文案 | 输入产品/活动信息和目标平台，生成适配的营销文案。 |

## 子技能索引

| 子技能 | 英文标识 | 文件 |
|--------|----------|------|
| SEO内容优化 | `seo-content-optimization` | [references/seo-content-optimization.md](./references/seo-content-optimization.md) |
| 品牌调性审查 | `brand-voice-review` | [references/brand-voice-review.md](./references/brand-voice-review.md) |
| 广告合规检查 | `ad-compliance-check` | [references/ad-compliance-check.md](./references/ad-compliance-check.md) |
| 活动策划 | `campaign-planning` | [references/campaign-planning.md](./references/campaign-planning.md) |
| 社媒热点追踪 | `social-media-trends` | [references/social-media-trends.md](./references/social-media-trends.md) |
| 竞品追踪 | `competitive-tracking` | [references/competitive-tracking.md](./references/competitive-tracking.md) |
| 营销效果分析 | `marketing-performance` | [references/marketing-performance.md](./references/marketing-performance.md) |
| 营销文案 | `copywriting` | [references/copywriting.md](./references/copywriting.md) |
## 跨技能协同指引

| 协同技能 | 典型场景 |
|---------|---------|
| 产品管理 | 文案撰写前先获取PRD确认产品定位和核心卖点 |

> 以上为推荐协同路径。执行复合任务时，请根据实际需求灵活组合。

## 变更日志

### v1.0.1 (2026-06-19)
- 对齐 description 子技能名与路由表名称
- 压缩路由表说明列至40字以内
- 新增跨技能协同指引章节
- 删除冗余英文 description 行