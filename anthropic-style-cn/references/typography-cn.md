# Typography CN

## 问题根源

很多英文优先设计系统会把拉丁字体放在前面，再让中文直接回退到系统黑体。结果是英文有明确品牌气质，中文却突然切换到另一套字形语言，混排非常割裂。

## 字体选型

### 霞鹜文楷

- 用于中文标题、引言、引用块
- 与 DM Serif 的书卷感相容
- 笔触更有温度，适合人文科技叙事

### 思源黑体

- 用于中文 UI、正文、说明文字
- 字符覆盖广，平台兼容性强
- 与 DM Sans 混排时更稳定

## 三种引入方式

### 1. CDN

```html
<link rel="preconnect" href="https://cdn.jsdelivr.net">
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/lxgw-wenkai-screen-webfont/style.css">
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@fontsource/source-sans-3@latest/400.css">
```

说明：适合原型或演示站，落地速度快。

### 2. 子集化离线

- 用 `pyftsubset` 或字体服务导出常用中文子集
- 标题和正文拆分两套文件
- 与本技能中的英文字体离线包一起部署

### 3. 纯系统字体

```css
--font-body-cn: "DM Sans", "PingFang SC", "Hiragino Sans GB", "Microsoft YaHei", "Noto Sans CJK SC", sans-serif;
```

说明：适合对包体极度敏感的后台系统。

## CSS Token 覆盖

```css
:root {
  --font-display-cn: "DM Serif Display", "LXGW WenKai", "STKaiti", serif;
  --font-body-cn: "DM Sans", "Source Han Sans SC", "PingFang SC", "Microsoft YaHei", sans-serif;
  --leading-cn-tight: 1.35;
  --leading-cn-normal: 1.75;
  --leading-cn-relaxed: 1.95;
}
```

## 混排字体栈写法

英文字体在前，中文字体在后：

```css
body {
  font-family: "DM Sans", "Source Han Sans SC", "PingFang SC", "Microsoft YaHei", sans-serif;
}

h1,
h2,
h3 {
  font-family: "DM Serif Display", "DM Serif Text", "LXGW WenKai", serif;
}
```

如果做更精细的自动分流，可对子集字体使用 `unicode-range`。

## 中文排版细节

- 标题字重优先 400 / 500，避免中文标题过黑
- 正文优先 400，注释和说明可用 300 或 400
- 中文正文行高通常高于英文，建议 1.75 左右
- 中文句号、逗号、顿号密集时，优先增加行高，不要盲目加字距
- 避免把整段中文设置成全大写风格的 letter-spacing
- 中英文之间建议保留自然空格，代码与正文之间用 Mono 字体明确分层
- 标点压缩交给浏览器默认排版，必要时配合 `text-spacing` 与内容审核

字号和行高搭配表：

| 场景 | 字号 | 行高 |
| --- | --- | --- |
| Hero 标题 | 48-64px | 1.15-1.2 |
| 一级标题 | 36-48px | 1.2-1.25 |
| 二级标题 | 28-36px | 1.25-1.3 |
| 正文 | 16-18px | 1.75 |
| 辅助说明 | 14px | 1.7 |
| 说明标签 | 12-13px | 1.5 |

## 各平台系统字体兜底链

```css
font-family:
  "DM Sans",
  "Source Han Sans SC",
  "PingFang SC",
  "Hiragino Sans GB",
  "Microsoft YaHei",
  "Noto Sans CJK SC",
  "WenQuanYi Micro Hei",
  sans-serif;
```

