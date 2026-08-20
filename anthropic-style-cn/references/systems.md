# Systems

## 1. Z-index 分层管理体系

### 问题根源

弹层、浮层、侧边栏和 Toast 常被临时硬编码 `z-index: 9999`。结果是组件互相打架，后续加一个新弹层就要继续叠数值，系统失控。

### 代码实现

```css
:root {
  --z-base: 0;
  --z-dropdown: 1000;
  --z-sticky: 1100;
  --z-overlay: 1200;
  --z-drawer: 1300;
  --z-modal: 1400;
  --z-popover: 1500;
  --z-toast: 1600;
  --z-command: 1700;
}

.app-header { z-index: var(--z-sticky); }
.dropdown { z-index: var(--z-dropdown); }
.overlay { z-index: var(--z-overlay); }
.drawer { z-index: var(--z-drawer); }
.modal { z-index: var(--z-modal); }
.toast-stack { z-index: var(--z-toast); }
.command-palette { z-index: var(--z-command); }
```

## 2. 响应式断点与移动端规范

### 问题根源

桌面优先的页面在移动端通常会变成“缩小版桌面站”，点击区过小、信息层级失真、阅读行长失控。

### 代码实现

```css
:root {
  --bp-sm: 36rem;
  --bp-md: 48rem;
  --bp-lg: 64rem;
  --bp-xl: 80rem;
}

.feature-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: var(--space-4);
}

.touch-target {
  min-height: 44px;
  min-width: 44px;
}

@media (min-width: 48rem) {
  .feature-grid {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }
}

@media (min-width: 64rem) {
  .feature-grid {
    grid-template-columns: repeat(3, minmax(0, 1fr));
  }
}
```

## 3. 暗色模式切换完整方案

### 问题根源

暗色模式最常见问题是闪白、状态不同步，以及组件颜色未 token 化导致深色模式破版。

### 代码实现

```html
<script>
  (function () {
    const saved = localStorage.getItem("theme");
    const systemDark = window.matchMedia("(prefers-color-scheme: dark)").matches;
    const theme = saved || (systemDark ? "dark" : "light");
    document.documentElement.dataset.theme = theme;
  })();
</script>
```

```js
const toggle = document.querySelector("[data-theme-toggle]");

toggle?.addEventListener("click", () => {
  const next = document.documentElement.dataset.theme === "dark" ? "light" : "dark";
  document.documentElement.dataset.theme = next;
  localStorage.setItem("theme", next);
});
```

## 4. CSS 动画性能规范

### 问题根源

直接动画 `width`、`height`、`top`、`left` 会触发布局和重绘，导致掉帧。页面会从“有温度”变成“有卡顿”。

### 代码实现

```css
.card {
  transition:
    transform var(--duration-base) var(--ease-standard),
    opacity var(--duration-base) var(--ease-standard);
}

.card:hover {
  transform: translateY(-3px);
}

.scroll-reveal {
  will-change: transform, opacity;
}
```

规则：

- 只动画 `transform` 与 `opacity`
- `will-change` 只给短时出现的动效元素
- 长列表避免所有项同时 reveal

## 5. Focus Trap

### 问题根源

Modal、Drawer、Command Palette 如果不锁焦点，键盘用户会把 Tab 焦点跳出弹层，造成上下文混乱。

### 代码实现

```js
export function createFocusTrap(container) {
  const selectors = [
    "a[href]",
    "button:not([disabled])",
    "textarea:not([disabled])",
    "input:not([disabled])",
    "select:not([disabled])",
    "[tabindex]:not([tabindex='-1'])"
  ].join(",");

  function onKeydown(event) {
    if (event.key !== "Tab") return;

    const focusable = [...container.querySelectorAll(selectors)];
    if (!focusable.length) return;

    const first = focusable[0];
    const last = focusable[focusable.length - 1];

    if (event.shiftKey && document.activeElement === first) {
      event.preventDefault();
      last.focus();
    } else if (!event.shiftKey && document.activeElement === last) {
      event.preventDefault();
      first.focus();
    }
  }

  container.addEventListener("keydown", onKeydown);
  const initial = container.querySelector(selectors);
  initial?.focus();

  return () => container.removeEventListener("keydown", onKeydown);
}
```

## 6. SVG 图标系统

### 问题根源

图标最容易出现尺寸、颜色和可访问性不统一。不同页面混用 PNG、彩色 SVG 和字体图标，维护成本极高。

### 代码实现

```html
<svg class="icon" width="20" height="20" viewBox="0 0 20 20" aria-hidden="true">
  <path d="M10 2 2 6v8l8 4 8-4V6Z" fill="none" stroke="currentColor" stroke-width="1.5" />
</svg>
```

```css
.icon {
  display: inline-block;
  color: inherit;
  flex: none;
}
```

规则：

- 使用 `currentColor`
- 装饰性图标加 `aria-hidden="true"`
- 需要读屏文本时，在旁边放可见或 `sr-only` 文本
- 如果做字体子集，使用 `unicode-range` 按语言拆分

## 7. 字体加载策略

### 问题根源

标题字体和 UI 字体都很有个性，一旦加载策略失误，就会产生闪白、CLS 抖动或首屏空白。

### 代码实现

```html
<link rel="preload" href="/assets/fonts/dm-serif-display-400.woff2" as="font" type="font/woff2" crossorigin>
<link rel="preload" href="/assets/fonts/dm-sans-400.woff2" as="font" type="font/woff2" crossorigin>
<link rel="stylesheet" href="/assets/fonts/fonts.css">
```

规则：

- 所有 `@font-face` 使用 `font-display: swap`
- 首屏只 preload 关键字重
- 中文大字体不内置，优先 CDN 或子集化

## 8. 滚动行为规范

### 问题根源

弹窗打开时页面跳动、背景仍可滚、iOS 回弹穿透，是产品体验里最常见的“廉价感来源”。

### 代码实现

```css
body.is-scroll-locked {
  overflow: hidden;
  padding-right: var(--scrollbar-compensation, 0px);
}

.scroll-region {
  overscroll-behavior: contain;
}
```

```js
export function lockScroll() {
  const scrollbar = window.innerWidth - document.documentElement.clientWidth;
  document.body.style.setProperty("--scrollbar-compensation", `${scrollbar}px`);
  document.body.classList.add("is-scroll-locked");
}

export function unlockScroll() {
  document.body.classList.remove("is-scroll-locked");
}
```

如果是超长列表，优先引入虚拟滚动容器，避免把数百行节点一次性塞进 DOM。

## 9. 表单验证完整模式

### 问题根源

只在提交时一次性报错会让用户挫败；只在输入时实时报错又会造成噪音。最佳方案是 `blur` 触发、`input` 清除、`submit` 全量校验。

### 代码实现

```js
const form = document.querySelector("[data-form]");

function validateField(field) {
  const error = field.nextElementSibling;
  if (!field.value.trim()) {
    field.setAttribute("aria-invalid", "true");
    error.textContent = "该字段不能为空";
    return false;
  }
  field.removeAttribute("aria-invalid");
  error.textContent = "";
  return true;
}

form?.querySelectorAll("[data-required]").forEach((field) => {
  field.addEventListener("blur", () => validateField(field));
  field.addEventListener("input", () => {
    if (field.value.trim()) validateField(field);
  });
});

form?.addEventListener("submit", (event) => {
  const fields = [...form.querySelectorAll("[data-required]")];
  const invalid = fields.filter((field) => !validateField(field));
  if (invalid.length) {
    event.preventDefault();
    invalid[0].focus();
  }
});
```

## 10. 图片优化规范

### 问题根源

品牌感页面容易依赖大量大图。若不区分 LCP 图片和普通内容图，首屏会慢、移动端带宽浪费严重。

### 代码实现

```html
<picture>
  <source
    type="image/webp"
    srcset="/images/hero@1x.webp 1x, /images/hero@2x.webp 2x">
  <img
    src="/images/hero@1x.jpg"
    srcset="/images/hero@1x.jpg 1x, /images/hero@2x.jpg 2x"
    alt="暖米色编辑风格的 MockMaster 首页展示"
    width="1200"
    height="900"
    fetchpriority="high">
</picture>
```

规则：

- WebP 优先
- 非首屏图再加 `loading="lazy"`
- LCP 图不要 lazy
- `alt` 描述内容与功能，不写“图片”“photo”

