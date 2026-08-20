# Logo

## Logo 构成原则

- 以圆角矩形、弧线和留白构成“技术产品中的人文出版物”气质
- 基础网格建议使用 8 × 8 或 12 × 12 方格
- 曲线转折使用有机圆角，避免机械直角
- 轮廓比例可参考黄金矩形，让标记更稳而不僵硬

## SVG 路径绘制思路

路径命令速查：

- `M`：移动到起点
- `L`：直线
- `H / V`：水平 / 垂直线
- `C`：三次贝塞尔曲线
- `Q`：二次贝塞尔曲线
- `A`：椭圆弧
- `Z`：闭合路径

示例：

```svg
<svg viewBox="0 0 120 120" fill="none" xmlns="http://www.w3.org/2000/svg">
  <rect x="12" y="12" width="96" height="96" rx="28" fill="currentColor" />
  <path d="M36 42C36 33.716 42.716 27 51 27H69C77.284 27 84 33.716 84 42V78C84 86.284 77.284 93 69 93H51C42.716 93 36 86.284 36 78V42Z" fill="var(--color-panel)" />
  <path d="M46 42H74V50H46V42ZM46 58H68V66H46V58Z" fill="currentColor" />
</svg>
```

## 品牌色用法

四种推荐方案：

1. 彩色主版：`--color-accent` + `--color-panel`
2. 反色版：深底 `--color-inverse` + 浅字 `--color-inverse-text`
3. 单色深版：全 `--color-heading`
4. 图标版：只保留外轮廓与内部切口

## 四个必备变体

- 彩色横版：品牌字 + 图标
- 反色横版：用于深色 Hero、页脚
- 单色图标版：用于水印、印章、Favicon 简化
- 小尺寸图标版：只保留最核心识别结构

## 最小尺寸与安全间距

- 横版最小宽度：120px
- 图标最小宽度：24px
- 安全间距至少等于图标圆角半径
- 不要在嘈杂纹理上直接放彩色 Logo，先加纯色承托层

## Favicon 多尺寸方案

建议导出：

- `favicon.svg`
- `favicon-16.png`
- `favicon-32.png`
- `apple-touch-icon.png` 180 × 180
- `android-chrome-192.png`
- `android-chrome-512.png`

SVG 自适应深色模式示例：

```svg
<svg viewBox="0 0 64 64" xmlns="http://www.w3.org/2000/svg">
  <style>
    .bg { fill: #c96f3b; }
    .fg { fill: #fffaf4; }
    @media (prefers-color-scheme: dark) {
      .bg { fill: #f4efe6; }
      .fg { fill: #171311; }
    }
  </style>
  <rect class="bg" x="6" y="6" width="52" height="52" rx="16" />
  <path class="fg" d="M20 22h24v6H20zm0 14h18v6H20z" />
</svg>
```

