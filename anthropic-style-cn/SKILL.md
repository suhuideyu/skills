---
name: anthropic-style-cn
description: Build or restyle Chinese-language web interfaces in an Anthropic-inspired visual system with warm beige backgrounds, serif-and-sans typography pairing, restrained orange accents, human-centered motion, and organic editorial layouts. Use when Codex needs to create design systems, landing pages, dashboards, product UIs, component libraries, or visual guidelines that should feel closer to anthropic.com than cold blue AI aesthetics, especially for Simplified Chinese products.
---

# Anthropic Style CN

按本技能构建中文前端时，始终优先使用 `references/base.css` 的 Token 和布局基线，再从 `references/components.md` 中选择组件骨架，最后根据 `references/systems.md`、`references/logo.md` 与 `references/typography-cn.md` 校正系统层规则。不要引入冷蓝色科技风、荧光渐变或过强玻璃拟态。

## 0. 设计哲学

核心矛盾是“技术性”与“人文温度”并存：

- 用清晰的结构、秩序化间距、稳定组件节奏体现技术可信度。
- 用暖米色背景、纸感区块、克制橙色点缀和衬线标题表达编辑感与人味。
- 让页面像一份会呼吸的数字出版物，而不是冷硬控制台。
- 在信息密度较高的产品页面中，优先用留白、节奏和排版层级解决复杂度，不依赖高饱和色块。

## 1. 颜色系统

先加载 `references/base.css`。主要 Token：

```css
:root {
  --color-bg: #f4efe6;
  --color-bg-soft: #fbf7f2;
  --color-panel: #fffaf4;
  --color-panel-strong: #f1e7d8;
  --color-text: #1f1a17;
  --color-text-muted: #5f574e;
  --color-heading: #171311;
  --color-border: #d9cbb8;
  --color-accent: #c96f3b;
  --color-accent-strong: #ab5727;
  --color-accent-soft: #ead7c4;
  --color-inverse: #14110f;
  --color-inverse-soft: #26211d;
}
```

深色模式切换使用 `data-theme="dark"`，不要改变量命名，只覆盖值。详见 `references/systems.md` 的暗色模式章节。

使用规则：

| 场景 | 推荐 Token | 说明 |
| --- | --- | --- |
| 页面底色 | `--color-bg` | 默认全局底色，营造暖纸感 |
| 主卡片 | `--color-panel` | 主要内容承载层 |
| 次级区块 | `--color-bg-soft` / `--color-panel-strong` | 拉开深浅节奏 |
| 强调按钮 | `--color-accent` | 只用于关键 CTA |
| 标题 | `--color-heading` | 保证衬线标题稳重 |
| 正文 | `--color-text` | 长文本主色 |
| 次要说明 | `--color-text-muted` | 元数据、辅助说明 |
| 反色深区 | `--color-inverse` | Dark CTA、页脚、重点收口区 |

## 2. 字体排版

### 英文方案 A

- 标题优先：`DM Serif Display` 或 `DM Serif Text`
- UI / 正文优先：`DM Sans`
- 代码优先：`JetBrains Mono`

### 中文方案 B

- 标题中文优先：`LXGW WenKai`
- UI / 正文中文优先：`Source Han Sans SC`
- 英文字体永远排在中文字体前，利用字形覆盖自然分流。

建议栈：

```css
--font-display: "DM Serif Display", "DM Serif Text", "LXGW WenKai", serif;
--font-body: "DM Sans", "Source Han Sans SC", "PingFang SC", "Microsoft YaHei", sans-serif;
--font-mono: "JetBrains Mono", "DM Sans", "Source Han Sans SC", monospace;
```

中文排版细节、引入方案和兜底链见 `references/typography-cn.md`。

## 3. 间距与布局

- 使用 4px 网格，所有尺寸优先落在 4 / 8 / 12 / 16 / 20 / 24 / 32 / 48 / 64 / 96 上。
- 内容容器最大宽度建议 1200px 到 1280px。
- 首屏 Hero 使用 5:3 或 8:5 栅格比例，而不是平均二分。
- 文章型页面优先 `minmax(0, 1.15fr) minmax(280px, 0.85fr)`，形成黄金比例式不对称分栏。
- 控件高度建议 40px、44px、52px 三档。

## 4. 核心组件规范

组件索引在 `references/components.md`，包含 35 个可直接复制的 HTML + CSS（含必要 JS）示例。使用顺序：

1. 从 `components.md` 选最近的组件骨架。
2. 将颜色全部替换为 `var(--color-*)`。
3. 用 `references/base.css` 的 Token 与工具类统一收口。
4. 需要弹层时复用 `systems.md` 的 Focus Trap。

## 5. 动效与交互

- 页面进入优先 `fadeUp`、`reveal`、`stagger`，时长 240ms 到 520ms。
- 鼠标悬停不做大幅放缩，优先 2px 到 4px 轻微位移和阴影变化。
- 按钮反馈要像纸上轻压，不像玻璃按钮弹跳。
- 列表内容进入建议使用 Stagger Reveal，每项延迟 30ms 到 60ms。
- 交互动画只使用 `transform` 和 `opacity`，详见 `references/systems.md`。

## 6. 背景与视觉深度

- 主背景以暖米色为基底，叠加极淡径向渐变或纹理噪点。
- 页面至少保留三层明度：页面底、面板层、深色收口层。
- 避免纯白通栏；让白更偏 `--color-panel`。
- 阴影尽量柔和，像纸张层叠，不要蓝色发光。

## 7. 可访问性规范

- 文本与背景对比度满足 WCAG AA。
- 所有交互元素都要有可见焦点环。
- Modal / Drawer / Command Palette 必须包含 Focus Trap。
- `prefers-reduced-motion` 下关闭复杂入场动画。
- 触摸目标最小 44px。

## 8. 反模式清单

以下行为禁止出现：

1. 用冷蓝色、荧光紫、赛博青做主色，因为会破坏 Anthropic 式温度。
2. 标题和正文都使用同一套无衬线体，因为会丢掉编辑感层次。
3. 大面积纯白背景，因为会削弱纸感。
4. 组件里直接写十六进制颜色，因为无法系统化换肤。
5. 过多磨砂玻璃和背景模糊，因为风格会偏科技演示页。
6. 超重阴影和强立体卡片，因为会显得廉价。
7. 高频跳动动画，因为会破坏克制感。
8. 信息密集区域仍使用居中排版，因为阅读效率差。
9. 深色模式直接反相，因为会丢失暖感。
10. 把所有区块做成相同圆角和相同背景，因为页面会失去节奏。

## 9. 系统性规范索引

打开 `references/systems.md`，按需读取：

- Z-index 分层体系
- 响应式与移动端规则
- 深色模式切换
- 动画性能边界
- Focus Trap
- SVG 图标系统
- 字体加载策略
- 滚动行为规范
- 表单验证模式
- 图片优化规范

## 10. Logo 绘制索引

品牌标识、SVG 绘制、Favicon 方案见 `references/logo.md`。

## 11. 简体中文排版索引

中文字体策略、混排规则和字号建议见 `references/typography-cn.md`。

