# A 深海科技 — 微信公众号模板

> 沉稳专业，适合深度分析/行业解读类文章。

## 色板

| 用途 | 色值 | 说明 |
|------|------|------|
| 主背景 | `#f7f8fa` | 浅灰底，正文区 |
| 深海军蓝 | `#1a1a2e` | 卡片背景、表头 |
| 金色 | `#f5a623` | 强调文字、数据、表头文字 |
| 章节红 | `#c41e3a` | 左侧色条、序号卡片 |
| 引用蓝 | `#5dade2` | 引用高亮左侧色条 |
| 引用绿 | `#27ae60` | 引用高亮左侧色条（正面/结论） |
| 浅灰 | `#e8e8e8` | 卡片内正文 |
| B端蓝底 | `#f0f7ff` | B端方案卡片 |
| C端红底 | `#fff5f5` | C端方案卡片 |
| 警示红底 | `#fff5f5` | 警示框背景 |
| 警示红框 | `#ffccc7` | 警示框边框 |
| 灰色卡片 | `#f8f9fa` | 序号结论卡片 |
| 图注灰 | `#999` | 配图说明文字 |

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
- 卡片圆角：`border-radius:8px`
- 章节标题左边距：`padding-left:12px`

## 模块清单（15个）

### 1. 导读卡片

```html
<section style="background-color:#1a1a2e;border-radius:8px;padding:20px;margin-bottom:16px;">
<p style="font-size:18px;font-weight:bold;color:#f5a623;margin-bottom:12px;margin-top:0;">导读</p>
<p style="font-size:16px;color:#e8e8e8;line-height:1.8;margin:0;">这里放文章导读内容，用一两句话概括核心观点。</p>
</section>
```

### 2. 章节标题

```html
<p style="font-size:18px;font-weight:bold;color:#333;border-left:4px solid #c41e3a;padding-left:12px;margin-top:24px;margin-bottom:16px;">第一章 章节标题</p>
```

### 3. 正文段落

```html
<p style="font-size:16px;color:#333;line-height:1.8;margin-bottom:16px;margin-top:0;">这里是正文段落内容。保持自然的行高和段落间距，阅读体验舒适。</p>
```

### 4. 引用高亮块（蓝色-数据/事实）

```html
<section style="background-color:#f7f8fa;border-left:4px solid #5dade2;padding:16px;margin-bottom:16px;border-radius:4px;">
<p style="font-size:16px;color:#555;line-height:1.8;margin:0;margin-top:0;">这里放引用内容、核心数据或关键事实。</p>
</section>
```

### 4b. 引用高亮块（绿色-正面/结论）

```html
<section style="background-color:#f7f8fa;border-left:4px solid #27ae60;padding:16px;margin-bottom:16px;border-radius:4px;">
<p style="font-size:16px;color:#555;line-height:1.8;margin:0;margin-top:0;">这里放正面观点或总结性结论。</p>
</section>
```

### 4c. 引用高亮块（红色-警示/冲突）

```html
<section style="background-color:#f7f8fa;border-left:4px solid #c41e3a;padding:16px;margin-bottom:16px;border-radius:4px;">
<p style="font-size:16px;color:#555;line-height:1.8;margin:0;margin-top:0;">这里放冲突性观点或需要警惕的信号。</p>
</section>
```

### 5. 深色数据卡片

```html
<section style="background-color:#1a1a2e;border-radius:8px;padding:20px;margin-bottom:16px;text-align:center;">
<p style="font-size:28px;font-weight:bold;color:#f5a623;margin:0 0 8px 0;">381</p>
<p style="font-size:16px;color:#e8e8e8;line-height:1.6;margin:0;">过去6年量产芯片数量</p>
</section>
```

### 6. 表格（深色表头）

```html
<table style="width:100%;border-collapse:collapse;margin-bottom:16px;font-family:-apple-system,BlinkMacSystemFont,'Helvetica Neue','PingFang SC','Hiragino Sans GB','Microsoft YaHei UI','Microsoft YaHei',Arial,sans-serif;">
<thead>
<tr style="background-color:#1a1a2e;">
<th style="padding:10px 12px;color:#f5a623;font-size:14px;font-weight:bold;text-align:left;border:1px solid #2a2a4e;">维度</th>
<th style="padding:10px 12px;color:#f5a623;font-size:14px;font-weight:bold;text-align:left;border:1px solid #2a2a4e;">内容</th>
<th style="padding:10px 12px;color:#f5a623;font-size:14px;font-weight:bold;text-align:left;border:1px solid #2a2a4e;">说明</th>
</tr>
</thead>
<tbody>
<tr><td style="padding:10px 12px;color:#333;font-size:13px;border:1px solid #eee;">维度一</td><td style="padding:10px 12px;color:#333;font-size:13px;border:1px solid #eee;">数据</td><td style="padding:10px 12px;color:#333;font-size:13px;border:1px solid #eee;">说明文字</td></tr>
<tr><td style="padding:10px 12px;color:#333;font-size:13px;border:1px solid #eee;">维度二</td><td style="padding:10px 12px;color:#333;font-size:13px;border:1px solid #eee;">数据</td><td style="padding:10px 12px;color:#333;font-size:13px;border:1px solid #eee;">说明文字</td></tr>
</tbody>
</table>
```

### 7. B端/C端对比色块

```html
<table style="width:100%;border-collapse:separate;border-spacing:8px;margin-bottom:16px;font-family:-apple-system,BlinkMacSystemFont,'Helvetica Neue','PingFang SC','Hiragino Sans GB','Microsoft YaHei UI','Microsoft YaHei',Arial,sans-serif;">
<tr>
<td style="background-color:#f0f7ff;border-radius:8px;padding:16px;width:50%;vertical-align:top;">
<p style="font-size:15px;font-weight:bold;color:#1a1a2e;margin:0 0 8px 0;">B端（企业）</p>
<p style="font-size:14px;color:#555;line-height:1.6;margin:0;">面向电科院/省调/地调等电力企业客户，强调合规与基线核查。</p>
</td>
<td style="background-color:#fff5f5;border-radius:8px;padding:16px;width:50%;vertical-align:top;">
<p style="font-size:15px;font-weight:bold;color:#1a1a2e;margin:0 0 8px 0;">C端（个人）</p>
<p style="font-size:14px;color:#555;line-height:1.6;margin:0;">面向个人开发者和小微企业，强调轻量级和易用性。</p>
</td>
</tr>
</table>
```

### 8. 三格亮点卡片

```html
<table style="width:100%;border-collapse:separate;border-spacing:8px;margin-bottom:16px;font-family:-apple-system,BlinkMacSystemFont,'Helvetica Neue','PingFang SC','Hiragino Sans GB','Microsoft YaHei UI','Microsoft YaHei',Arial,sans-serif;">
<tr>
<td style="background-color:#f0f7ff;border-radius:8px;padding:16px;width:33%;text-align:center;vertical-align:middle;">
<p style="font-size:28px;margin:0 0 4px 0;">⚡</p>
<p style="font-size:14px;font-weight:bold;color:#1a1a2e;margin:0;">亮点一</p>
<p style="font-size:12px;color:#999;margin:4px 0 0 0;">描述</p>
</td>
<td style="background-color:#f5f5f5;border-radius:8px;padding:16px;width:33%;text-align:center;vertical-align:middle;">
<p style="font-size:28px;margin:0 0 4px 0;">🔒</p>
<p style="font-size:14px;font-weight:bold;color:#1a1a2e;margin:0;">亮点二</p>
<p style="font-size:12px;color:#999;margin:4px 0 0 0;">描述</p>
</td>
<td style="background-color:#f0fff5;border-radius:8px;padding:16px;width:34%;text-align:center;vertical-align:middle;">
<p style="font-size:28px;margin:0 0 4px 0;">🎯</p>
<p style="font-size:14px;font-weight:bold;color:#1a1a2e;margin:0;">亮点三</p>
<p style="font-size:12px;color:#999;margin:4px 0 0 0;">描述</p>
</td>
</tr>
</table>
```

### 9. 警示框

```html
<section style="background-color:#fff5f5;border:1px solid #ffccc7;border-radius:8px;padding:16px;margin-bottom:16px;">
<p style="font-size:15px;font-weight:bold;color:#c41e3a;margin:0 0 8px 0;">⚠️ 注意</p>
<p style="font-size:14px;color:#555;line-height:1.6;margin:0;">这里放需要读者特别注意的警示内容或风险提示。</p>
</section>
```

### 10. 序号结论卡片

```html
<table style="width:100%;border-collapse:collapse;margin-bottom:16px;font-family:-apple-system,BlinkMacSystemFont,'Helvetica Neue','PingFang SC','Hiragino Sans GB','Microsoft YaHei UI','Microsoft YaHei',Arial,sans-serif;">
<tr>
<td style="background-color:#f8f9fa;border-left:4px solid #c41e3a;padding:16px;border-radius:0 8px 8px 0;">
<p style="font-size:15px;font-weight:bold;color:#1a1a2e;margin:0 0 8px 0;">结论一：核心观点</p>
<p style="font-size:14px;color:#555;line-height:1.6;margin:0;">这里放结论的详细描述，可以是一段话。</p>
</td>
</tr>
</table>
```

### 11. 结尾总结卡片

```html
<section style="background-color:#1a1a2e;border-radius:8px;padding:20px;margin-bottom:16px;margin-top:24px;">
<p style="font-size:18px;font-weight:bold;color:#f5a623;margin-bottom:12px;margin-top:0;">写在最后</p>
<p style="font-size:16px;color:#e8e8e8;line-height:1.8;margin:0;">这里放文章总结，与导读卡片首尾呼应，形成闭环。</p>
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
<span style="display:inline-block;width:40px;height:2px;background-color:#c41e3a;vertical-align:middle;"></span>
<span style="display:inline-block;width:8px;height:8px;background-color:#c41e3a;border-radius:50%;margin:0 8px;vertical-align:middle;"></span>
<span style="display:inline-block;width:40px;height:2px;background-color:#c41e3a;vertical-align:middle;"></span>
</p>
```

### 14. 配图+图注

```html
<img src="https://mmbiz.qpic.cn/mmbiz_png/xxxxxx/0" style="width:100%;border-radius:8px;display:block;margin-bottom:8px;" alt="配图" />
<p style="font-size:12px;color:#999;text-align:center;margin-top:0;margin-bottom:16px;">配图说明：这里是图片的描述文字</p>
```

### 15. 引导关注卡片

```html
<section style="background-color:#1a1a2e;border-radius:8px;padding:20px;margin-bottom:16px;text-align:center;">
<p style="font-size:18px;font-weight:bold;color:#f5a623;margin:0 0 8px 0;">关注「六一的AI人生记录仪」</p>
<p style="font-size:14px;color:#e8e8e8;line-height:1.6;margin:0;">记录 AI 时代的每天。从业者的眼睛，普通人的话。</p>
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
