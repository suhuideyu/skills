# Components

以下组件默认已加载 `base.css` 与 `assets/fonts/fonts.css`。

## 基础组件（10）

### 1. Hero 区块

```html
<section class="hero surface container">
  <div class="hero-copy">
    <p class="eyebrow">Anthropic Style</p>
    <h1 class="display">让 AI 产品像一份有温度的出版物。</h1>
    <p class="muted">用暖米色、衬线标题和克制橙色点缀，表达可信而克制的智能体验。</p>
    <div class="hero-actions">
      <a class="btn btn-primary" href="#">开始设计</a>
      <a class="btn btn-secondary" href="#">查看规范</a>
    </div>
  </div>
  <div class="hero-card surface">
    <div class="hero-metric"><strong>35</strong><span>组件</span></div>
    <div class="hero-metric"><strong>10</strong><span>系统规则</span></div>
    <div class="hero-metric"><strong>CN</strong><span>中文优先</span></div>
  </div>
</section>
```

```css
.hero {
  display: grid;
  grid-template-columns: minmax(0, 1.15fr) minmax(280px, 0.85fr);
  gap: var(--space-8);
  padding: var(--space-10);
}
.hero-copy { display: grid; gap: var(--space-5); }
.hero-actions { display: flex; gap: var(--space-3); flex-wrap: wrap; }
.hero-card { padding: var(--space-8); display: grid; gap: var(--space-4); align-content: center; }
.hero-metric strong { display: block; font: 400 var(--text-4xl)/1 var(--font-display); color: var(--color-heading); }
.hero-metric span { color: var(--color-text-muted); }
```

### 2. Feature Grid 特性卡片

```html
<section class="feature-grid">
  <article class="feature-card surface">
    <h3>暖感视觉</h3>
    <p>背景、排版和留白像编辑页面，而非冷蓝色仪表盘。</p>
  </article>
  <article class="feature-card surface">
    <h3>系统统一</h3>
    <p>所有颜色和圆角都来自 Token，而不是临时硬编码。</p>
  </article>
  <article class="feature-card surface">
    <h3>中文友好</h3>
    <p>中英混排不割裂，阅读节奏更稳定。</p>
  </article>
</section>
```

```css
.feature-grid { display: grid; grid-template-columns: repeat(3, minmax(0, 1fr)); gap: var(--space-5); }
.feature-card { padding: var(--space-6); display: grid; gap: var(--space-3); }
.feature-card h3 { font: 400 var(--text-2xl)/1.2 var(--font-display-alt); color: var(--color-heading); }
```

### 3. Stats 统计数字

```html
<div class="stats surface">
  <div><strong>92%</strong><span>完成率</span></div>
  <div><strong>4.8</strong><span>满意度</span></div>
  <div><strong>12m</strong><span>平均时长</span></div>
</div>
```

```css
.stats { display: grid; grid-template-columns: repeat(3, 1fr); gap: var(--space-4); padding: var(--space-6); text-align: center; }
.stats strong { display: block; font: 400 var(--text-4xl)/1 var(--font-display); }
.stats span { color: var(--color-text-muted); }
```

### 4. Blockquote 引用块

```html
<blockquote class="quote surface">
  <p>“真正好的 AI 界面不是更像机器，而是更像值得信任的文字作品。”</p>
  <footer>MockMaster Design Notes</footer>
</blockquote>
```

```css
.quote { padding: var(--space-8); border-left: 4px solid var(--color-accent); display: grid; gap: var(--space-4); }
.quote p { font: 400 var(--text-2xl)/var(--leading-cn-normal) var(--font-display-alt); }
.quote footer { color: var(--color-text-muted); }
```

### 5. Pricing 价格卡片

```html
<div class="pricing-grid">
  <article class="pricing-card surface">
    <h3>Starter</h3>
    <p class="price">¥49<span>/月</span></p>
    <ul role="list"><li>基础组件</li><li>排版规范</li><li>暗色模式</li></ul>
    <button class="btn btn-secondary">选择方案</button>
  </article>
</div>
```

```css
.pricing-grid { display: grid; gap: var(--space-5); }
.pricing-card { padding: var(--space-6); display: grid; gap: var(--space-4); max-width: 320px; }
.price { font: 400 var(--text-4xl)/1 var(--font-display); color: var(--color-heading); }
.price span { font: 400 var(--text-md)/1 var(--font-body); color: var(--color-text-muted); }
```

### 6. CTA Dark 深色行动区

```html
<section class="cta-dark surface-dark container">
  <div>
    <p class="eyebrow">Ready</p>
    <h2 class="display">把你的 AI 产品重新做得更像“作品”。</h2>
  </div>
  <a class="btn btn-primary" href="#">立即开始</a>
</section>
```

```css
.cta-dark { padding: var(--space-10); display: flex; justify-content: space-between; align-items: center; gap: var(--space-6); }
.cta-dark .display { color: var(--color-inverse-text); }
```

### 7. Footer 页脚

```html
<footer class="site-footer surface-dark">
  <div class="container footer-inner">
    <strong>MockMaster</strong>
    <nav aria-label="页脚导航">
      <a href="#">产品</a><a href="#">文档</a><a href="#">联系</a>
    </nav>
  </div>
</footer>
```

```css
.site-footer { padding: var(--space-8) 0; }
.footer-inner { display: flex; justify-content: space-between; gap: var(--space-4); color: var(--color-inverse-text); }
.footer-inner nav { display: flex; gap: var(--space-4); }
```

### 8. Code Block 代码块

```html
<pre class="code-block"><code>const theme = document.documentElement.dataset.theme;
if (theme === "dark") enableWarmContrast();</code></pre>
```

```css
.code-block {
  padding: var(--space-6);
  border-radius: var(--radius-lg);
  background: var(--color-inverse);
  color: var(--color-inverse-text);
  font: 400 var(--text-sm)/1.8 var(--font-mono);
  overflow-x: auto;
}
```

### 9. Toast 通知条

```html
<div class="toast" role="status" aria-live="polite">
  <span>主题已切换到暖米色深色模式。</span>
  <button aria-label="关闭通知">关闭</button>
</div>
```

```css
.toast {
  position: fixed;
  right: var(--space-4);
  bottom: var(--space-4);
  z-index: var(--z-toast);
  display: flex;
  gap: var(--space-3);
  align-items: center;
  padding: var(--space-4) var(--space-5);
  background: var(--color-inverse);
  color: var(--color-inverse-text);
  border-radius: 999px;
}
```

### 10. Skeleton 骨架屏

```html
<div class="skeleton-card surface" aria-hidden="true">
  <div class="skeleton skeleton-line"></div>
  <div class="skeleton skeleton-line short"></div>
  <div class="skeleton skeleton-block"></div>
</div>
```

```css
.skeleton-card { padding: var(--space-6); display: grid; gap: var(--space-4); }
.skeleton { border-radius: var(--radius-sm); background: linear-gradient(90deg, var(--color-panel-strong), var(--color-panel), var(--color-panel-strong)); background-size: 200% 100%; animation: shimmer 1.2s linear infinite; }
.skeleton-line { height: 16px; }
.skeleton-line.short { width: 55%; }
.skeleton-block { height: 120px; }
@keyframes shimmer { to { background-position: -200% 0; } }
```

## 导航与结构（5）

### 11. Sidebar 侧边栏

```html
<aside class="sidebar surface" aria-label="侧边导航">
  <a class="sidebar-brand" href="#">MockMaster</a>
  <nav class="sidebar-nav">
    <a class="is-active" href="#">概览</a>
    <a href="#">面试记录</a>
    <a href="#">资源中心</a>
  </nav>
</aside>
```

```css
.sidebar { width: 240px; min-height: 100vh; padding: var(--space-6); display: grid; align-content: start; gap: var(--space-6); }
.sidebar-nav { display: grid; gap: var(--space-2); }
.sidebar-nav a { padding: 0.75rem 1rem; border-radius: var(--radius-md); color: var(--color-text-muted); }
.sidebar-nav .is-active { background: var(--color-accent-soft); color: var(--color-heading); }
```

### 12. Tabs 标签页

```html
<div class="tabs" role="tablist" aria-label="视图切换">
  <button role="tab" aria-selected="true" class="is-active">概览</button>
  <button role="tab" aria-selected="false">分析</button>
  <button role="tab" aria-selected="false">设置</button>
</div>
```

```css
.tabs { display: inline-flex; gap: var(--space-2); padding: var(--space-1); background: var(--color-panel-strong); border-radius: 999px; }
.tabs button { min-height: 40px; padding: 0 var(--space-4); border-radius: 999px; color: var(--color-text-muted); }
.tabs .is-active { background: var(--color-panel); color: var(--color-heading); box-shadow: var(--shadow-sm); }
```

### 13. Breadcrumb 面包屑

```html
<nav aria-label="面包屑" class="breadcrumb">
  <a href="#">首页</a>
  <span>/</span>
  <a href="#">规范</a>
  <span>/</span>
  <span aria-current="page">组件</span>
</nav>
```

```css
.breadcrumb { display: flex; gap: var(--space-2); align-items: center; color: var(--color-text-muted); }
.breadcrumb [aria-current="page"] { color: var(--color-heading); }
```

### 14. Pagination 分页

```html
<nav aria-label="分页" class="pagination">
  <button aria-label="上一页">←</button>
  <button class="is-active" aria-current="page">1</button>
  <button>2</button>
  <button>3</button>
  <button aria-label="下一页">→</button>
</nav>
```

```css
.pagination { display: flex; gap: var(--space-2); }
.pagination button { min-width: 44px; min-height: 44px; border-radius: 999px; background: var(--color-panel); border: 1px solid var(--color-border); }
.pagination .is-active { background: var(--color-accent); color: var(--color-inverse-text); border-color: var(--color-accent); }
```

### 15. Dropdown 下拉菜单

```html
<div class="dropdown-wrap">
  <button class="btn btn-secondary" aria-haspopup="menu" aria-expanded="false" data-dropdown-trigger>筛选</button>
  <div class="dropdown surface" role="menu" hidden>
    <button role="menuitem">最近 7 天</button>
    <button role="menuitem">最近 30 天</button>
    <button role="menuitem">全部</button>
  </div>
</div>
```

```css
.dropdown-wrap { position: relative; display: inline-block; }
.dropdown { position: absolute; top: calc(100% + 8px); left: 0; min-width: 180px; padding: var(--space-2); z-index: var(--z-dropdown); }
.dropdown button { width: 100%; text-align: left; padding: 0.75rem 1rem; border-radius: var(--radius-sm); }
.dropdown button:hover { background: var(--color-bg-soft); }
```

```js
const trigger = document.querySelector("[data-dropdown-trigger]");
const menu = document.querySelector(".dropdown");
trigger?.addEventListener("click", () => {
  const open = !menu.hasAttribute("hidden");
  menu.toggleAttribute("hidden", open);
  trigger.setAttribute("aria-expanded", String(!open));
});
```

## 表单与交互（5）

### 16. Form 完整表单

```html
<form class="form surface" data-form novalidate>
  <label>姓名<input class="input" data-required aria-describedby="name-error"></label>
  <p class="muted" id="name-error" aria-live="polite"></p>
  <label>邮箱<input class="input" type="email" data-required aria-describedby="email-error"></label>
  <p class="muted" id="email-error" aria-live="polite"></p>
  <label>目标岗位<select class="select"><option>前端开发</option></select></label>
  <label>补充信息<textarea class="textarea"></textarea></label>
  <button class="btn btn-primary" type="submit">提交</button>
</form>
```

```css
.form { max-width: 560px; padding: var(--space-6); display: grid; gap: var(--space-3); }
.form label { display: grid; gap: var(--space-2); color: var(--color-heading); }
```

### 17. Toggle / Switch 开关

```html
<label class="switch">
  <span>暗色模式</span>
  <button class="switch-control" type="button" role="switch" aria-checked="false">
    <span class="switch-thumb"></span>
  </button>
</label>
```

```css
.switch { display: flex; align-items: center; gap: var(--space-4); }
.switch-control { width: 56px; height: 32px; padding: 4px; border-radius: 999px; background: var(--color-panel-strong); }
.switch-thumb { display: block; width: 24px; height: 24px; border-radius: 50%; background: var(--color-panel); transition: transform var(--duration-base) var(--ease-standard); }
.switch-control[aria-checked="true"] { background: var(--color-accent); }
.switch-control[aria-checked="true"] .switch-thumb { transform: translateX(24px); }
```

```js
document.querySelector(".switch-control")?.addEventListener("click", (event) => {
  const next = event.currentTarget.getAttribute("aria-checked") !== "true";
  event.currentTarget.setAttribute("aria-checked", String(next));
});
```

### 18. Tooltip 气泡提示

```html
<button class="tooltip-trigger" aria-describedby="tip-1">悬停查看</button>
<span id="tip-1" role="tooltip" class="tooltip">用于解释术语和小型提示。</span>
```

```css
.tooltip-trigger { position: relative; color: var(--color-accent-strong); }
.tooltip {
  display: inline-block;
  margin-left: var(--space-2);
  padding: 0.5rem 0.75rem;
  border-radius: var(--radius-sm);
  background: var(--color-inverse);
  color: var(--color-inverse-text);
  font-size: var(--text-sm);
}
```

### 19. Modal 弹窗

```html
<button class="btn btn-primary" data-open-modal>打开弹窗</button>
<div class="overlay" hidden></div>
<div class="modal surface" role="dialog" aria-modal="true" aria-labelledby="modal-title" hidden>
  <h2 id="modal-title" class="display">确认保存本次更改？</h2>
  <p class="muted">你可以稍后继续完善，但当前内容会先落盘。</p>
  <div class="modal-actions">
    <button class="btn btn-secondary" data-close-modal>取消</button>
    <button class="btn btn-primary">确认</button>
  </div>
</div>
```

```css
.overlay { position: fixed; inset: 0; background: rgb(20 17 15 / 0.4); z-index: var(--z-overlay); }
.modal { position: fixed; inset: 50% auto auto 50%; transform: translate(-50%, -50%); z-index: var(--z-modal); width: min(520px, calc(100vw - 2rem)); padding: var(--space-6); display: grid; gap: var(--space-4); }
.modal-actions { display: flex; justify-content: flex-end; gap: var(--space-3); }
```

```js
import { createFocusTrap } from "./focus-trap.js";
const openModal = document.querySelector("[data-open-modal]");
const closeModal = document.querySelector("[data-close-modal]");
const modal = document.querySelector(".modal");
const overlay = document.querySelector(".overlay");
let releaseModalTrap;
function showModal() {
  modal.hidden = false;
  overlay.hidden = false;
  releaseModalTrap = createFocusTrap(modal);
}
function hideModal() {
  modal.hidden = true;
  overlay.hidden = true;
  releaseModalTrap?.();
}
openModal?.addEventListener("click", showModal);
closeModal?.addEventListener("click", hideModal);
overlay?.addEventListener("click", hideModal);
```

### 20. Accordion 折叠面板

```html
<div class="accordion surface">
  <button class="accordion-trigger" aria-expanded="false" aria-controls="acc-1">如何应用到 Vue 项目？</button>
  <div id="acc-1" hidden>
    <p>先引入 base.css，再把组件骨架映射成你的框架组件。</p>
  </div>
</div>
```

```css
.accordion { padding: var(--space-4); }
.accordion-trigger { width: 100%; text-align: left; font-weight: 500; color: var(--color-heading); }
#acc-1 { padding-top: var(--space-3); color: var(--color-text-muted); }
```

```js
document.querySelector(".accordion-trigger")?.addEventListener("click", (event) => {
  const button = event.currentTarget;
  const panel = document.getElementById(button.getAttribute("aria-controls"));
  const expanded = button.getAttribute("aria-expanded") === "true";
  button.setAttribute("aria-expanded", String(!expanded));
  panel.hidden = expanded;
});
```

## 内容展示（5）

### 21. Table 数据表格

```html
<div class="table-wrap surface">
  <table class="table">
    <thead><tr><th>用户</th><th>岗位</th><th>状态</th></tr></thead>
    <tbody><tr><td>林岚</td><td>前端开发</td><td>已完成</td></tr></tbody>
  </table>
</div>
```

```css
.table-wrap { overflow: auto; padding: var(--space-4); }
.table { width: 100%; border-collapse: collapse; }
.table th, .table td { padding: 0.875rem 1rem; border-bottom: 1px solid var(--color-border); text-align: left; }
.table th { color: var(--color-text-muted); font-weight: 500; }
```

### 22. Timeline 时间线

```html
<ol class="timeline" role="list">
  <li><strong>09:00</strong><p>开始面试</p></li>
  <li><strong>09:12</strong><p>进入追问阶段</p></li>
  <li><strong>09:20</strong><p>完成面试</p></li>
</ol>
```

```css
.timeline { display: grid; gap: var(--space-4); }
.timeline li { position: relative; padding-left: var(--space-6); }
.timeline li::before { content: ""; position: absolute; left: 8px; top: 0.55rem; width: 10px; height: 10px; border-radius: 50%; background: var(--color-accent); }
.timeline li::after { content: ""; position: absolute; left: 12px; top: 1.25rem; bottom: -1.2rem; width: 1px; background: var(--color-border); }
.timeline li:last-child::after { display: none; }
```

### 23. Empty State 空状态

```html
<section class="empty-state surface">
  <h3 class="display">还没有任何结果</h3>
  <p class="muted">从一次完整面试开始，记录会在这里沉淀。</p>
  <a class="btn btn-primary" href="#">开始面试</a>
</section>
```

```css
.empty-state { padding: var(--space-10); text-align: center; display: grid; gap: var(--space-4); place-items: center; }
```

### 24. Banner / Alert 提示横幅

```html
<div class="banner" role="alert">
  <strong>系统提示：</strong>
  <span>只有完整完成的面试才会进入历史记录。</span>
</div>
```

```css
.banner {
  display: flex;
  gap: var(--space-3);
  padding: var(--space-4) var(--space-5);
  border-radius: var(--radius-lg);
  background: var(--color-accent-soft);
  color: var(--color-heading);
}
```

### 25. Step Indicator 步骤条

```html
<ol class="steps" role="list">
  <li class="is-current"><span>1</span> 选择岗位</li>
  <li><span>2</span> 设定时长</li>
  <li><span>3</span> 开始面试</li>
</ol>
```

```css
.steps { display: flex; gap: var(--space-4); flex-wrap: wrap; }
.steps li { display: inline-flex; align-items: center; gap: var(--space-2); color: var(--color-text-muted); }
.steps span { width: 28px; height: 28px; display: inline-grid; place-items: center; border-radius: 50%; background: var(--color-panel-strong); }
.steps .is-current { color: var(--color-heading); }
.steps .is-current span { background: var(--color-accent); color: var(--color-inverse-text); }
```

## 补充高频组件（10）

### 26. Avatar 头像组

```html
<div class="avatar-group" aria-label="参与者">
  <img src="https://placehold.co/40x40" alt="林岚">
  <img src="https://placehold.co/40x40" alt="程野">
  <span>+4</span>
</div>
```

```css
.avatar-group { display: flex; align-items: center; }
.avatar-group > * { width: 40px; height: 40px; border-radius: 50%; border: 2px solid var(--color-panel); margin-left: -8px; background: var(--color-accent-soft); display: grid; place-items: center; }
.avatar-group > *:first-child { margin-left: 0; }
```

### 27. Progress Bar / Ring 进度条

```html
<div class="progress-bar" aria-label="完成进度" aria-valuemin="0" aria-valuemax="100" aria-valuenow="68" role="progressbar">
  <span style="width:68%"></span>
</div>
<svg class="progress-ring" viewBox="0 0 120 120" role="img" aria-label="68% 完成">
  <circle cx="60" cy="60" r="48" class="track"></circle>
  <circle cx="60" cy="60" r="48" class="value"></circle>
</svg>
```

```css
.progress-bar { width: 220px; height: 10px; border-radius: 999px; background: var(--color-panel-strong); overflow: hidden; }
.progress-bar span { display: block; height: 100%; background: var(--color-accent); }
.progress-ring { width: 88px; height: 88px; }
.progress-ring .track { fill: none; stroke: var(--color-panel-strong); stroke-width: 10; }
.progress-ring .value { fill: none; stroke: var(--color-accent); stroke-width: 10; stroke-linecap: round; stroke-dasharray: 301.6; stroke-dashoffset: 96.5; transform: rotate(-90deg); transform-origin: 60px 60px; }
```

### 28. Search 搜索框带联想

```html
<div class="search-box">
  <label class="sr-only" for="search">搜索</label>
  <input id="search" class="input" autocomplete="off" aria-autocomplete="list" aria-expanded="true" aria-controls="search-list" placeholder="搜索岗位或资源">
  <ul id="search-list" class="search-suggest surface" role="listbox">
    <li role="option">前端开发工程师</li>
    <li role="option">Mock 面试规范</li>
  </ul>
</div>
```

```css
.search-box { position: relative; max-width: 360px; }
.search-suggest { position: absolute; inset: calc(100% + 8px) 0 auto; padding: var(--space-2); display: grid; gap: var(--space-1); }
.search-suggest li { padding: 0.75rem 1rem; border-radius: var(--radius-sm); }
.search-suggest li:hover { background: var(--color-bg-soft); }
```

### 29. Command Palette ⌘K 面板

```html
<div class="command-shell" hidden>
  <div class="overlay"></div>
  <section class="command-palette surface" role="dialog" aria-modal="true" aria-labelledby="command-title">
    <h2 id="command-title" class="sr-only">命令面板</h2>
    <input class="input" placeholder="输入命令或页面名称">
    <ul role="list">
      <li><button>打开历史记录</button></li>
      <li><button>切换深色模式</button></li>
    </ul>
  </section>
</div>
```

```css
.command-palette { position: fixed; top: 10vh; left: 50%; transform: translateX(-50%); width: min(680px, calc(100vw - 2rem)); padding: var(--space-4); z-index: var(--z-command); display: grid; gap: var(--space-3); }
.command-palette ul { display: grid; gap: var(--space-1); }
.command-palette button { width: 100%; text-align: left; padding: 0.875rem 1rem; border-radius: var(--radius-md); }
```

```js
import { createFocusTrap } from "./focus-trap.js";
const shell = document.querySelector(".command-shell");
let releaseCommandTrap;
window.addEventListener("keydown", (event) => {
  if ((event.metaKey || event.ctrlKey) && event.key.toLowerCase() === "k") {
    event.preventDefault();
    shell.hidden = false;
    releaseCommandTrap = createFocusTrap(document.querySelector(".command-palette"));
  }
  if (event.key === "Escape" && !shell.hidden) {
    shell.hidden = true;
    releaseCommandTrap?.();
  }
});
```

### 30. Drawer 侧滑抽屉

```html
<div class="drawer-shell" hidden>
  <div class="overlay"></div>
  <aside class="drawer surface" role="dialog" aria-modal="true" aria-labelledby="drawer-title">
    <h2 id="drawer-title" class="display">筛选项</h2>
    <button class="btn btn-secondary">关闭</button>
  </aside>
</div>
```

```css
.drawer { position: fixed; top: 0; right: 0; width: min(420px, 100vw); height: 100vh; z-index: var(--z-drawer); padding: var(--space-6); border-radius: 0; display: grid; align-content: start; gap: var(--space-4); }
```

```js
import { createFocusTrap } from "./focus-trap.js";
const drawer = document.querySelector(".drawer");
let releaseDrawerTrap = createFocusTrap(drawer);
```

### 31. Chip / Tag 可删除标签

```html
<div class="chip-row">
  <span class="chip">前端开发<button aria-label="删除标签">×</button></span>
  <span class="chip">20 分钟<button aria-label="删除标签">×</button></span>
</div>
```

```css
.chip-row { display: flex; gap: var(--space-2); flex-wrap: wrap; }
.chip { display: inline-flex; align-items: center; gap: var(--space-2); padding: 0.5rem 0.75rem; border-radius: 999px; background: var(--color-accent-soft); color: var(--color-heading); }
```

### 32. Popover 浮层卡片

```html
<div class="popover-wrap">
  <button class="btn btn-secondary" aria-haspopup="dialog" aria-expanded="true">查看详情</button>
  <div class="popover surface" role="dialog">
    <strong>面试建议</strong>
    <p class="muted">优先补充项目结果与量化指标。</p>
  </div>
</div>
```

```css
.popover-wrap { position: relative; display: inline-block; }
.popover { position: absolute; top: calc(100% + 8px); left: 0; width: 260px; padding: var(--space-4); z-index: var(--z-popover); display: grid; gap: var(--space-2); }
```

### 33. Carousel 轮播

```html
<section class="carousel surface" aria-roledescription="carousel">
  <div class="carousel-track">
    <article class="carousel-slide is-active">第一张卡片</article>
    <article class="carousel-slide">第二张卡片</article>
  </div>
  <div class="carousel-actions">
    <button aria-label="上一张">←</button>
    <button aria-label="下一张">→</button>
  </div>
</section>
```

```css
.carousel { padding: var(--space-6); display: grid; gap: var(--space-4); }
.carousel-track { display: grid; }
.carousel-slide { display: none; min-height: 180px; border-radius: var(--radius-lg); background: var(--color-bg-soft); padding: var(--space-6); }
.carousel-slide.is-active { display: block; }
.carousel-actions { display: flex; gap: var(--space-2); justify-content: flex-end; }
```

```js
const slides = [...document.querySelectorAll(".carousel-slide")];
let index = 0;
function renderSlide() {
  slides.forEach((slide, i) => slide.classList.toggle("is-active", i === index));
}
document.querySelectorAll(".carousel-actions button")[1]?.addEventListener("click", () => {
  index = (index + 1) % slides.length;
  renderSlide();
});
document.querySelectorAll(".carousel-actions button")[0]?.addEventListener("click", () => {
  index = (index - 1 + slides.length) % slides.length;
  renderSlide();
});
```

### 34. Context Menu 右键菜单

```html
<div class="context-target surface">右键我</div>
<div class="context-menu surface" role="menu" hidden>
  <button role="menuitem">复制链接</button>
  <button role="menuitem">重命名</button>
</div>
```

```css
.context-target { padding: var(--space-6); }
.context-menu { position: fixed; padding: var(--space-2); z-index: var(--z-popover); min-width: 180px; }
.context-menu button { width: 100%; text-align: left; padding: 0.75rem 1rem; border-radius: var(--radius-sm); }
```

```js
const target = document.querySelector(".context-target");
const contextMenu = document.querySelector(".context-menu");
target?.addEventListener("contextmenu", (event) => {
  event.preventDefault();
  contextMenu.hidden = false;
  contextMenu.style.left = `${event.clientX}px`;
  contextMenu.style.top = `${event.clientY}px`;
});
window.addEventListener("click", () => { contextMenu.hidden = true; });
```

### 35. FAB 悬浮按钮

```html
<button class="fab" aria-label="快速新建">＋</button>
```

```css
.fab {
  position: fixed;
  right: var(--space-5);
  bottom: var(--space-5);
  width: 56px;
  height: 56px;
  border-radius: 50%;
  background: var(--color-accent);
  color: var(--color-inverse-text);
  box-shadow: var(--shadow-lg);
}
```

