# 微信公众号运营系统 — AI Agent Onboarding

> 版本：v8.0（2026-08-11 复盘优化）｜ 公众号：六一的AI人生记录仪（ID: <WECHAT_ID>）

---

## 一、项目概述

公众号「六一的AI人生记录仪」全流程运营系统，覆盖从选题到推送的完整链路。

- **公众号名称**：六一的AI人生记录仪
- **公众号ID**：<WECHAT_ID>
- **内容领域**：AI / 智能体 / AI 安全
- **发布频率**：日更（半自动）—— AI 写 / 排 / 推草稿；人工负责：选题、标题拍板、IP 白名单、群发、配图
- **品牌调性**：专业不枯燥、有温度有观点。人格：AI 行业多年的老朋友，懂行不端着，敢说真话
- **品牌口号**：「记录 AI 时代的每天。」
- **写作视角**：第一人称对话式，AI 从业者视角，必出个人观点（khazix 仅为文末署名，非号主）

### 三类风格桶（选题先定桶，再写）

写作前必须先把文章归到以下三类之一，桶不同写法完全不同。**派 copywriter 时 prompt 必须显式标【桶X】+ 对应写作范式**，否则默认套 khazix 母规范导致串味（8/4 国标即因此翻车）。完整定义见 `.workbuddy/memory/MEMORY.md` 的「三类风格桶与写作范式」节。

| 桶 | 驱动 | 写作范式要点 | 字数 | 占比 |
|----|------|------------|------|------|
| **桶1 热点追踪风** | 事件驱动（发布/安全事件/政策） | 客观陈述为主 + 简短点评；用媒体原口径禁拟人化；**硬禁翻案句**；定语写全 + 标阶段 | 3000-3500 纯汉字 | 主体（60+ 篇） |
| **桶2 观点共鸣风（嘴替心声）** | 主题驱动（持续命题/行业判断） | 全篇「你」视角；三拍结构（痛诉→翻转→钉句）；金句 14-16 句含具体物件；先痛诉后判断 | 3000-3500 纯汉字 | 人设 + 转化 |
| **桶3 技术解读风** | 机制驱动（技术/机制深扒） | 不用 khazix，客观复盘风；背景→机制→细节→启示→总结；信源一手零编造 | 4000-6000 含标点 | ≤1 篇/周（第四支柱） |

---

## 二、项目目录结构（对齐实际）

```
zimeiti/
├── agent.md                         # 本文件 — AI Agent 项目 Onboarding（v8.0）
├── README.md                        # 系统使用指南
├── 工作流文档-v3.0.md               # 历史工作流文档（7步，已被本 v8.0 取代，保留参考）
├── MULTIAGENT_WORKFLOW.md           # 多 Agent 协作增强工作流（含第一性原理+红队审查）
├── main.sh                          # 主控脚本（状态管理）
├── config/
│   └── .env.credentials.yaml        # 微信 API 凭证（含 access_token，gitignore）
├── content/
│   └── YYYY-MM-DD-slug/             # 每篇文章一个目录
│       ├── metadata.json            # 标题/摘要/作者（标题唯一源，禁止硬编码）
│       ├── article.md               # 正文 Markdown（禁写 # 标题 H1，防重复标题）
│       ├── article.html             # 微信兼容 HTML 排版（零 div 单 p 整块）
│       ├── cover.png                # 封面图 1280x720
│       ├── angle.md                 # 创意策划方案（占质量 60%）
│       └── research.md              # 素材调研（5类信源）
├── templates/
│   └── article_template.html        # 排版根模板（零 div 单 p 整块，标准色值表）
├── brand-identity/
│   └── 品牌标识材料.md              # 完整品牌资产
├── scripts/
│   └── publish/
│       ├── wechat_push.py           # ⭐ 标准化推送脚本（--dir 自动读 html/cover/metadata）
│       ├── wechat_token.sh          # Token 刷新
│       └── publish_prompt.md        # 发布指令
├── data/                            # 热点/草稿/分析数据
├── generated-images/                # AI 生图缓存
└── .workbuddy/
    ├── memory/
    │   ├── MEMORY.md                # 长期记忆（写作规范/三类风格桶/排版铁律/防错清单/API踩坑）
    │   └── YYYY-MM-DD.md            # 每日工作日志
    └── skills/                      # 项目级技能
```

---

## 三、核心工作流 v8.0（8 步 + 三类风格桶）

> 复盘来源：v7.5 → v8.0，固化 8 月踩坑（排版翻车 / IP 白名单 / 重复标题 / 翻案句返工）+ 三类风格桶。

```
选题(四维+三塔+定桶) → angle(占质量60%) → 标题(3组ABC→metadata)
   → 文案(copywriter+标桶+check_prose) → 封面(ImageGen 1280x720先预览)
   → HTML(零div单p整块+自检) → 6.5 预览gate(硬) → 7 推送(定版→推→清旧稿)
   → 8 评论巡查(群发后1-3天)
```

### Step 1 选题（四维评分 + 三塔 + 先定桶）
- WebSearch 采集 AI 热点（≥5 条）
- 四维评分：热度 / 反差 / 价值 / 素材
- 三塔配比：流量 40% / 人设 30% / 转化 30%，不连续同类
- **新增（v8.0）**：选题同时定「风格桶」（热点/观点/技术解读），桶决定后续写法

### Step 2 创意策划（angle，占质量 60%）
- 输出 `angle.md`：角度 / 反差（第 4 个反共识角）/ 类比 / 情绪曲线
- 低频深度篇可走多 Agent：派 creative-strategist 做策划（见 MULTIAGENT_WORKFLOW.md）

### Step 3 标题定稿（铁律）
- 给 3 组：A 数据冲击 / B 场景画面 / C 紧迫警告，**C 型首选**
- 用户选定后写入 `metadata.json`：`{"title":"...","digest":"...","author":"六一"}`
- **铁律**：推送 title/digest 必须从 metadata.json 读，禁止硬编码

### Step 4 文案撰写（copywriter + 标桶 + check_prose）
- **派 copywriter 时 prompt 必须标【桶X】+ 写作范式**（防混写，根因修复 8/11）
- khazix 观点文母规范 / 技术解读第四支柱二选一（按桶）
- 产出 `article.md`；跑 `check_prose.py article.md`（翻案句/黑话/模型路标须 0）
- **⚠️ article.md 禁写 `# 标题` H1**：会被 md→html 渲染成 article.html 第一个 22px bold `<p>`，与微信头条撞车显示两次（8/10 踩坑）

### Step 5 封面图
- ImageGen 英文 prompt，1280x720 横版，**先预览确认再 cp cover.png**
- 去平台水印（hy-image-v3.0 本环境未暴露，珀西用 ImageGen 替代，裁切去水印）

### Step 6 HTML 排版（零 div 单 p 整块 + 自检）
- `cp templates/article_template.html content/.../article.html` 后填内容
- 色块一律单 `<p>` 整块（background/border/padding 写在 p 上 + `<br>` 换行），**禁 div**（8/5-8/6 翻车根因：div 背景微信渲染异常）
- 标准色值表（MEMORY 有完整版，禁自创）
- **推送前必删 article.html 第一个 `<p>`**（若它是 22px bold 标题）—— 防重复标题（8/10）
- 9/9 自检 + check_prose 全 0

### Step 6.5 发布前预览 gate（硬 ⭐）
- `present_files` 展示 article.html + cover.png，列层次清单
- **用户核对 OK 才推**，否则回头改

### Step 7 推送（定版 → 推 → 清旧稿）
```bash
env -u HTTPS_PROXY -u HTTP_PROXY -u https_proxy -u http_proxy NO_PROXY="*" \
  /opt/homebrew/bin/python3 scripts/publish/wechat_push.py --dir content/YYYY-MM-DD-slug
```
- Python 内 `os.environ.pop()` 清代理（微信 API 须直连）
- **重推前必须先删旧草稿**（脚本不支持删，用 `POST cgi-bin/draft/delete` + 旧 media_id），防草稿箱堆积混淆（8/10）
- 草稿创建后用户到后台 → 草稿箱 → 手动群发（订阅号 48001 限制）

### Step 8 发布后评论巡查（群发后 1-3 天）
- 看留言互动，四级判定（事实/逻辑/品牌/读者反驳），不阻塞 1-7

---

## 四、HTML 排版铁律（零 div 单 p 整块）

- **零 div**：色块一律单 `<p>` 整块（background/border/padding 写在 p 上 + `<br>` 换行），div 背景微信渲染异常
- 全内联样式；无 DOCTYPE/html 注释/ul-li/flex/gradient；font-weight 用 bold；code 内禁 font-size
- 外层 `<section max-width:680px;margin:0 auto>` 居中（仅 1 个 section 容器）
- **标准色值表（禁自创）**：开头浅橙卡 `#fffaf0`+金边 `#f5a623`；浅蓝卡 `#f0f7ff`+蓝边 `#5dade2`；盾块 `#f0fff4`+绿边 `#1e8449` / 矛块 `#fff5f5`+红边 `#c41e3a`；深色卡 `#1a1a2e`+金边 `#f5a623`+文字 `#e8e8e8`；H2 红左 border `#c41e3a`
- 结尾两卡深色 `#1a1a2e`+金边，**p 必须带 color:#e8e8e8**（深字压深底）；「写在最后」金句金色；「关注我」标题金色，第二行固定「六一的 AI 人生记录仪，一个做了快十年 AI 安全的老朋友」
- 8 项自检：class/DOCTYPE/注释/flex/gradient/ul-li/grid/div 全 0；section 平衡（仅 1 个外层）

> 完整色值表与防漂移规则见 MEMORY.md「HTML 排版铁律」节。

---

## 五、防错硬检查清单（13 项 · 每篇 Step 7 前逐条过，不过不推）

| # | 检查点 | 类别 |
|---|--------|------|
| ① | 日期 grep 零命中（中文大写/跨年核对） | 文字 |
| ② | 禁 khazix 自称 + 禁自我引用（我这号/本号/号主） | 文字 |
| ③ | 二手无拟人化演绎（用媒体原口径） | 文字 |
| ④ | 定语写全 + 标阶段（计划下达≠已实施） | 文字 |
| ⑤ | 时间线主宾不颠倒 | 文字 |
| ⑥ | 零 div 单 p 整块 | 排版 |
| ⑦ | 8 项自检全 0 + section 平衡 | 排版 |
| ⑧ | 结尾两卡 color:#e8e8e8 + 金标 | 排版 |
| ⑨ | check_prose 全 0（翻案句/黑话/模型路标） | 文字 |
| ⑩ | article.html 第一个 `<p>` 非 22px bold 标题（防重复标题） | 排版 |
| ⑪ | metadata 核对（title/digest 从 metadata 读，禁硬编码） | 推送 |
| ⑫ | 定版决策 + 旧稿清理（draft/delete API） | 推送 |
| ⑬ | IP 白名单（报错 IP 为准加白，建议加段防 NAT 轮换） | 推送 |

---

## 六、关键技术笔记

### 微信兼容排版
- 全内联样式（微信过滤 class 和 `<style>`）
- `background-color` 代替 `background`；font-weight 数字 → bold
- ul/li → `<p>•`；linear-gradient → `<strong>`+color；引用块 → section/`<p>`+border-left
- 封面只通过 API `thumb_media_id` 传，不在正文里

### API 规范
- 凭证：`config/.env.credentials.yaml`（含 access_token，脚本自动刷新）
- 封面上传：`material/add_material?type=image`
- 草稿创建：`cgi-bin/draft/add`；删旧稿：`cgi-bin/draft/delete`（body `{"media_id":"..."}`）
- 订阅号无法 API 群发，只能创建草稿后手动发

### 推送代理处理（铁律）
```python
for k in ['HTTP_PROXY','HTTPS_PROXY','http_proxy','https_proxy']:
    os.environ.pop(k, None)
```
`NO_PROXY` 对 Python urllib 不完全生效，必须用 `os.environ.pop()`。运行环境需用 `dangerouslyDisableSandbox: true` 绕开沙箱网络限制。

---

## 七、历史踩坑速查

| 日期 | 错误 | 教训 |
|------|------|------|
| 5.22 | HTML 用 class+style 被微信过滤 | 全内联样式 |
| 5.25 | 图片中文 prompt 被拦截 / 图片水印顽固 | 统一英文 prompt；正文不再配图，改组件库 |
| 5.27 | 标题错用上一篇的 / 跳过标题备选直接写 | metadata.json 统一管理 + 自检 #0 |
| 5.29 | HTML 用 DOCTYPE/div/注释 / font-family 没重复 | 纯正文无外壳、单 p、每标签带字体栈 |
| **8.5-8.6** | **div 背景微信渲染异常** | 改用**零 div 单 p 整块**（background 写 p 上） |
| **8.7** | **出口 IP 运营商 NAT 轮换被微信拦** | 以报错 IP 为准加白；建议加段防轮换（如 `<IP_CIDR>`）；清代理重推 |
| **8.10** | **article.md 的 H1 标题被渲染成 html 第一个 22px bold p，与微信头条撞车显示两次** | 推送前必删 article.html 第一个 22px bold `<p>`；写文禁 `# 标题` H1 |
| **8.4** | **国标篇翻案句 5 处未清（check_prose 不过）返工** | 热点桶禁用观点文强判断/翻案句写法（根因：桶分了写法没分）；固化为三类风格桶混写禁令 |
| **8.11** | **三类风格桶写法未分，热点/观点共鸣混用母规范** | 选题先定桶，派 copywriter 标【桶X】+ 写作范式 |

---

## 八、多 Agent 协作（低频深度篇）

- 日常轻量文（khazix 3000-3500 字）：主理人直写更快，不开团
- 低频深度/技术解读篇：走专家团正式铁律（TeamCreate 主理人建团 → 派发 → 中转 → 回传），可叠加红队审查
- 协作细节、第一性原理约束、红队五维清单见 `MULTIAGENT_WORKFLOW.md`
- 子 agent **无 working_memory**，品牌规范/风格铁律/写作范式**必须显式写进派发 prompt**

---

## 九、第一次执行指南

1. 读本文件（agent.md v8.0）全面了解项目
2. 读 `.workbuddy/memory/MEMORY.md` —— **重点看「三类风格桶与写作范式」「HTML 排版铁律」「防错硬检查清单」三节**
3. 读 `.workbuddy/memory/YYYY-MM-DD.md` 了解近期工作日志与待办
4. 读 `brand-identity/品牌标识材料.md` 了解品牌调性
5. 读 `MULTIAGENT_WORKFLOW.md` 了解多 Agent 协作（低频深度篇用）
6. 排版前 Read `templates/article_template.html` 对齐标准色值，禁每期自创格式
7. 开始执行任务（选题 → … → 推送，逐 Step 过防错清单）

---

> 最后更新：2026-08-11 | 版本 v8.0（复盘优化：三类风格桶 + 零 div 单 p 排版 + 13 项防错 + 8 月踩坑固化）
>
> 📌 **写作风格唯一对照表已独立成文件**：`style-guide.md`（三类风格桶 + khazix 铁律 + 排版/可视化层次 + 13 项防错 + 8 步速查）。写文前直接照此表执行，本文件同类章节如与 `style-guide.md` 冲突以它为准。
