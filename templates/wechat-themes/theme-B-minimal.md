# B 极简留白 — 微信公众号模板

> 干净克制，适合教程/攻略/观点评论类文章。

## 色板

| 用途 | 色值 | 说明 |
|------|------|------|
| 主背景 | `#ffffff` | 纯白底 |
| 正文色 | `#333333` | 主文字 |
| 强调色 | `#4285f4` | Google蓝，章节标题/链接/高亮 |
| 辅助色 | `#34a853` | 绿色，正面/结论引用 |
| 警示色 | `#ea4335` | 红色，警示/冲突引用 |
| 浅灰底 | `#f8f9fa` | 卡片背景 |
| 中灰 | `#5f6368` | 次要文字/图注 |
| 深灰 | `#202124` | 标题/强调文字 |
| 边框灰 | `#dadce0` | 表格边框/分隔线 |
| 引用蓝底 | `#e8f0fe` | 蓝色引用块背景 |
| 引用绿底 | `#e6f4ea` | 绿色引用块背景 |
| 警示红底 | `#fce8e6` | 警示框背景 |
| 表格交替 | `#fafbfc` | 表格行交替色 |
| 金色数据 | `#f5a623` | 数据卡片中的核心数字 |

## 字体

| 元素 | 字号 | 字重 |
|------|------|------|
| 正文 | 16px | normal |
| 小标题/卡片标题 | 18px | bold |
| 表格/卡片数据 | 14px | bold（数据行） |
| 表格正文 | 13px | normal |
| 图注 | 12px | normal |

**字体栈**：`-apple-system,BlinkMacSystemFont,'Helvetica Neue','PingFang SC','Hiragino Sans GB','Microsoft YaHei UI','Microsoft YaHei',Arial,sans-serif`

## 间距

- 正文段落间距：`margin-bottom:16px`
- 紧凑段落：`margin-bottom:12px`
- 卡片内边距：`padding:20px`（大卡片）、`padding:16px`（引用块）、`padding:10px 12px`（表格单元格）
- 卡片圆角：`border-radius:8px`（与A保持一致）
- 章节标题左边距：`padding-left:12px`

## 模块清单（15个）

### 1. 导读卡片

```html
<section style="background-color:#f8f9fa;border-radius:8px;padding:20px;margin-bottom:16px;border-left:4px solid #4285f4;">
<p style="font-size:15px;font-weight:bold;color:#202124;margin-bottom:12px;margin-top:0;">导读</p>
<p style="font-size:15px;color:#5f6368;line-height:1.8;margin:0;">这里放文章导读内容，简洁明了地概括核心观点。</p>
</section>
```

### 2. 章节标题

```html
<p style="font-size:18px;font-weight:bold;color:#202124;border-left:4px solid #4285f4;padding-left:12px;margin-top:24px;margin-bottom:16px;">第一章 章节标题</p>
```

### 3. 正文段落

```html
<p style="font-size:16px;color:#333333;line-height:1.8;margin-bottom:16px;margin-top:0;">这里是正文段落内容。纯白背景上，灰色文字阅读舒适，保持自然的行高和段落间距。</p>
```

### 4. 引用高亮块（蓝色-数据/事实）

```html
<section style="background-color:#e8f0fe;border-left:4px solid #4285f4;padding:16px;margin-bottom:16px;border-radius:4px;">
<p style="font-size:15px;color:#1a73e8;line-height:1.8;margin:0;margin-top:0;">这里放引用内容、核心数据或关键事实。</p>
</section>
```

### 4b. 引用高亮块（绿色-正面/结论）

```html
<section style="background-color:#e6f4ea;border-left:4px solid #34a853;padding:16px;margin-bottom:16px;border-radius:4px;">
<p style="font-size:15px;color:#137333;line-height:1.8;margin:0;margin-top:0;">这里放正面观点或总结性结论。</p>
</section>
```

### 4c. 引用高亮块（红色-警示/冲突）

```html
<section style="background-color:#fce8e6;border-left:4px solid #ea4335;padding:16px;margin-bottom:16px;border-radius:4px;">
<p style="font-size:15px;color:#c5221f;line-height:1.8;margin:0;margin-top:0;">这里放冲突性观点或需要警惕的信号。</p>
</section>
```

### 5. 深色数据卡片

```html
<section style="background-color:#202124;border-radius:8px;padding:20px;margin-bottom:16px;text-align:center;">
<p style="font-size:28px;font-weight:bold;color:#f5a623;margin:0 0 8px 0;">381</p>
<p style="font-size:15px;color:#e8e8e8;line-height:1.6;margin:0;">过去6年量产芯片数量</p>
</section>
```

### 6. 表格（蓝色表头）

```html
<table style="width:100%;border-collapse:collapse;margin-bottom:16px;font-family:-apple-system,BlinkMacSystemFont,'Helvetica Neue','PingFang SC','Hiragino Sans GB','Microsoft YaHei UI','Microsoft YaHei',Arial,sans-serif;">
<thead>
<tr style="background-color:#4285f4;">
<th style="padding:10px 12px;color:#ffffff;font-size:14px;font-weight:bold;text-align:left;border:1px solid #e0e0e0;">维度</th>
<th style="padding:10px 12px;color:#ffffff;font-size:14px;font-weight:bold;text-align:left;border:1px solid #e0e0e0;">内容</th>
<th style="padding:10px 12px;color:#ffffff;font-size:14px;font-weight:bold;text-align:left;border:1px solid #e0e0e0;">说明</th>
</tr>
</thead>
<tbody>
<tr><td style="padding:10px 12px;color:#333;font-size:13px;border:1px solid #dadce0;">维度一</td><td style="padding:10px 12px;color:#333;font-size:13px;border:1px solid #dadce0;">数据</td><td style="padding:10px 12px;color:#333;font-size:13px;border:1px solid #dadce0;">说明文字</td></tr>
<tr style="background-color:#fafbfc;"><td style="padding:10px 12px;color:#333;font-size:13px;border:1px solid #dadce0;">维度二</td><td style="padding:10px 12px;color:#333;font-size:13px;border:1px solid #dadce0;">数据</td><td style="padding:10px 12px;color:#333;font-size:13px;border:1px solid #dadce0;">说明文字</td></tr>
<tr><td style="padding:10px 12px;color:#333;font-size:13px;border:1px solid #dadce0;">维度三</td><td style="padding:10px 12px;color:#333;font-size:13px;border:1px solid #dadce0;">数据</td><td style="padding:10px 12px;color:#333;font-size:13px;border:1px solid #dadce0;">说明文字</td></tr>
</tbody>
</table>
```

### 7. B端/C端对比色块

```html
<table style="width:100%;border-collapse:separate;border-spacing:8px;margin-bottom:16px;font-family:-apple-system,BlinkMacSystemFont,'Helvetica Neue','PingFang SC','Hiragino Sans GB','Microsoft YaHei UI','Microsoft YaHei',Arial,sans-serif;">
<tr>
<td style="background-color:#e8f0fe;border-radius:8px;padding:16px;width:50%;vertical-align:top;">
<p style="font-size:15px;font-weight:bold;color:#1a73e8;margin:0 0 8px 0;">方案 A</p>
<p style="font-size:14px;color:#5f6368;line-height:1.6;margin:0;">面向企业级客户，强调安全合规与深度集成能力。</p>
</td>
<td style="background-color:#fce8e6;border-radius:8px;padding:16px;width:50%;vertical-align:top;">
<p style="font-size:15px;font-weight:bold;color:#c5221f;margin:0 0 8px 0;">方案 B</p>
<p style="font-size:14px;color:#5f6368;line-height:1.6;margin:0;">面向中小客户，强调轻量部署和快速见效。</p>
</td>
</tr>
</table>
```

### 8. 三格亮点卡片

```html
<table style="width:100%;border-collapse:separate;border-spacing:8px;margin-bottom:16px;font-family:-apple-system,BlinkMacSystemFont,'Helvetica Neue','PingFang SC','Hiragino Sans GB','Microsoft YaHei UI','Microsoft YaHei',Arial,sans-serif;">
<tr>
<td style="background-color:#e8f0fe;border-radius:8px;padding:16px;width:33%;text-align:center;vertical-align:middle;">
<p style="font-size:28px;margin:0 0 4px 0;">⚡</p>
<p style="font-size:14px;font-weight:bold;color:#1a73e8;margin:0;">亮点一</p>
<p style="font-size:12px;color:#5f6368;margin:4px 0 0 0;">描述</p>
</td>
<td style="background-color:#f8f9fa;border-radius:8px;padding:16px;width:33%;text-align:center;vertical-align:middle;">
<p style="font-size:28px;margin:0 0 4px 0;">🔒</p>
<p style="font-size:14px;font-weight:bold;color:#202124;margin:0;">亮点二</p>
<p style="font-size:12px;color:#5f6368;margin:4px 0 0 0;">描述</p>
</td>
<td style="background-color:#e6f4ea;border-radius:8px;padding:16px;width:34%;text-align:center;vertical-align:middle;">
<p style="font-size:28px;margin:0 0 4px 0;">🎯</p>
<p style="font-size:14px;font-weight:bold;color:#137333;margin:0;">亮点三</p>
<p style="font-size:12px;color:#5f6368;margin:4px 0 0 0;">描述</p>
</td>
</tr>
</table>
```

### 9. 警示框

```html
<section style="background-color:#fce8e6;border:1px solid #f5c6cb;border-radius:8px;padding:16px;margin-bottom:16px;">
<p style="font-size:15px;font-weight:bold;color:#c5221f;margin:0 0 8px 0;">⚠️ 注意</p>
<p style="font-size:14px;color:#5f6368;line-height:1.6;margin:0;">这里放需要读者特别注意的警示内容或风险提示。</p>
</section>
```

### 10. 序号结论卡片

```html
<table style="width:100%;border-collapse:collapse;margin-bottom:16px;font-family:-apple-system,BlinkMacSystemFont,'Helvetica Neue','PingFang SC','Hiragino Sans GB','Microsoft YaHei UI','Microsoft YaHei',Arial,sans-serif;">
<tr>
<td style="background-color:#f8f9fa;border-left:4px solid #4285f4;padding:16px;border-radius:0 8px 8px 0;">
<p style="font-size:15px;font-weight:bold;color:#202124;margin:0 0 8px 0;">结论一：核心观点</p>
<p style="font-size:14px;color:#5f6368;line-height:1.6;margin:0;">这里放结论的详细描述，可以是一段话。</p>
</td>
</tr>
</table>
```

### 11. 结尾总结卡片

```html
<section style="background-color:#f8f9fa;border-radius:8px;padding:20px;margin-bottom:16px;margin-top:24px;border-left:4px solid #4285f4;">
<p style="font-size:15px;font-weight:bold;color:#202124;margin-bottom:12px;margin-top:0;">写在最后</p>
<p style="font-size:15px;color:#5f6368;line-height:1.8;margin:0;">这里放文章总结，与导读卡片首尾呼应，形成闭环。</p>
</section>
```

### 12. 封面图区域

```html
<img src="https://mmbiz.qpic.cn/mmbiz_png/xxxxxx/0" style="width:100%;border-radius:8px;display:block;margin-bottom:8px;" alt="封面图" />
<p style="font-size:12px;color:#999;text-align:center;margin-top:0;margin-bottom:16px;">图注文字：图片说明</p>
```

### 13. 分隔线

```html
<p style="text-align:center;margin:24px 0;">
<span style="display:inline-block;width:40px;height:2px;background-color:#4285f4;vertical-align:middle;"></span>
<span style="display:inline-block;width:8px;height:8px;background-color:#4285f4;border-radius:50%;margin:0 8px;vertical-align:middle;"></span>
<span style="display:inline-block;width:40px;height:2px;background-color:#4285f4;vertical-align:middle;"></span>
</p>
```

### 14. 配图+图注

```html
<img src="https://mmbiz.qpic.cn/mmbiz_png/xxxxxx/0" style="width:100%;border-radius:8px;display:block;margin-bottom:8px;" alt="配图" />
<p style="font-size:12px;color:#999;text-align:center;margin-top:0;margin-bottom:16px;">配图说明：这里是图片的描述文字</p>
```

### 15. 引导关注卡片

```html
<section style="background-color:#f8f9fa;border-radius:8px;padding:20px;margin-bottom:16px;text-align:center;border-left:4px solid #4285f4;">
<p style="font-size:18px;font-weight:bold;color:#202124;margin:0 0 8px 0;">关注「六一的AI人生记录仪」</p>
<p style="font-size:14px;color:#5f6368;line-height:1.6;margin:0;">记录 AI 时代的每天。从业者的眼睛，普通人的话。</p>
</section>
```

## 微信兼容检查表

| # | 检查项 | 标准 |
|---|--------|------|
| 1 | class 属性 | 0 个 |
| 2 | `<style>` 标签 | 0 个 |
| 3 | flex 布局 | 0 处（用 table 替代） |
| 4 | grid 布局 | 0 处 |
| 5 | `<div>` 标签 | 0 个（用 `<section>` / `<table>`） |
| 6 | `<ul>`/`<li>`/`<ol>` | 0 个（用 `<p>` + `•` 替代） |
| 7 | background 简写 | 0 处（必须用 `background-color:`） |
| 8 | 正文无标题/元信息 | 由 API 字段渲染，正文不含标题 |
