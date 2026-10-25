# 大厂设计规范里的细节规则（已核对原文）

> 用途：给 AI 做 UI 时当"细节清单"。每条后面标了出处，[经验] 表示业界通用做法、非某家官方原文。
> 整理日期：2026-10

---

## 一、深色模式（最容易做出 AI 味的地方）

### 1. 白字黑底会"显粗"，要调的是字重，不是字号
- 原理：光渗错觉（irradiation illusion）——同样字重，浅字深底看起来更粗、更胖。
- 正确做法：深色模式下把字重**稍微调细**（如正文 400→350，或可变字体的 GRAD 轴调到约 -50）。
- 不建议改字号/字距：会让文字重新换行、布局跳动。字体设计师讨论里也认为字距只能辅助，解决不了"显粗"。
- CSS 示例（字体需支持 GRAD 轴，如 Roboto Flex；不支持就用可变 wght 微调）：
  ```css
  body { --GRAD: 0; font-variation-settings: "GRAD" var(--GRAD); }
  @media (prefers-color-scheme: dark) { body { --GRAD: -50; } }
  @media (prefers-color-scheme: dark) and (prefers-contrast: more) { body { --GRAD: 150; } }
  ```
- 数值依字体而定，切换明暗对比"看起来一样粗"为准。
- 出处：nerdy.dev（Adam Argyle）、TypeDrawers 字体设计师讨论

### 2. 背景不要纯黑、颜色不是简单反色
- Material：深色基底用 **#121212**（深灰），不是 #000。
- Apple：深色不是浅色的反转，"有些颜色反转了，有些没有"；要用语义色，不要写死色值。
- IBM Carbon 深色主题背景：Gray 90 **#262626** / Gray 100 **#161616**。
- 出处：Material Dark Theme、Apple HIG Dark Mode、Carbon Color

### 3. 深色下"越靠前越亮"，用亮度表示层级，而不是阴影
- 深色背景上阴影几乎看不见，所以层级靠表面变亮：
  - Material 2：在 #121212 上叠半透明白，4dp 叠 9%、8dp 叠 12%（层级越高越亮）。
  - Apple iOS：两套背景，base（更暗，往后退）和 elevated（更亮，往前进），弹窗/模态会自动用 elevated。
  - Carbon：深色主题每加一层就亮一级（Gray 100 → 90 → 80 → 70）；**深色主题里不要放比背景还暗的组件**。
  - 浅色主题反过来：Carbon 浅色是白 / Gray 10 交替，不靠变暗。
- Fluent（微软）：深色下阴影透明度要加大（低层阴影 14% → 28%），否则看不出。

### 4. 文字分层用透明度（Material）
- 白字在深色上：主要文字 **87%**、次要 **60%**、禁用 **38%**。
- Apple 对应：primary / secondary / tertiary / quaternary 四级 label 色。

### 5. 彩色要降饱和度
- 高饱和色在深色背景上会"发颤"、刺眼。
- Material：深色主色用 **200 色阶**（较淡的那档），色阶 50–400 最适合深色。
- 主色只用在 1–2 个品牌元素上（logo、主按钮）。
- Ant Design：深色模式"避免高对比的颜色或内容"，长时间看容易疲劳；信息层级要和浅色一致。

### 6. 图片和图标要单独处理
- 白底图片放在深色界面里会"发光"——稍微压暗。（Apple）
- 深色图标在深色背景上看不清时，加一圈细描边；有些图标需要分别准备明/暗两版。（Apple）
- 插画在深色下要降饱和、调整灰阶。（Material）

### 7. 对比度
- 最低 **4.5:1**（WCAG AA 正文）；Apple 建议自定义颜色争取 **7:1**，尤其是小字。
- 大字（≥24px）3:1，图形/图表元素 3:1。（Carbon）
- 要在"提高对比度""降低透明度"系统开关下也测一遍。（Apple）

### 8. 交互状态在明暗下方向相反（Carbon）
- 悬停：深色背景的元素变亮，浅色背景的元素变暗（半级）。
- 按下：两级；选中：一级。
- 焦点框：2px，浅色主题用 Blue 60，深色主题用白色，对比度至少 3:1。
- 禁用：一律用灰色系，不响应 hover/focus。

### 9. 跟随系统
- Apple：**不要在 App 里单独做一个明暗开关**，应跟随系统设置（网页可以提供开关，但默认要跟随 `prefers-color-scheme`）。
- 要支持"自动"模式：用户使用中途可能切换。

---

## 二、字体排版

- **字号底线**（Apple）：iOS 默认 17pt / 最小 11pt；macOS 默认 13pt / 最小 10pt。
- **避免细字重**：Ultralight、Thin、Light 小字号下看不清，用 Regular/Medium/Semibold/Bold。（Apple）
- **字体种类越少越好**，混用太多会打乱层级、显得没设计过。（Apple）
- **字距跟字号走**：字越小字距越大，字越大字距越紧（大标题要收紧字距）。Apple 系统字体有一张按字号变化的字距表。
- **行距**：密集界面用紧凑行距，大段阅读用宽松行距（Apple：紧 -2pt / 松 +2pt）。
- **数字用等宽数字**：表格、价格、计时器里的数字用 `font-variant-numeric: tabular-nums`，否则数字变化时会左右跳。[经验]
- **中文**：正文行高约 1.6–1.8，比英文宽松；中英混排时英文和数字两侧加间距（或靠字体自带处理）。[经验]

---

## 三、动效

### 时长（随移动距离/面积增大而变长——Material 和 Carbon 都这么规定）
| 用途 | Carbon | Material 3 |
|---|---|---|
| 按钮、开关等微交互 | 70ms | 50–100ms |
| 淡入淡出 | 110ms | 150–200ms |
| 小范围展开/短距离移动 | 150ms | 200–300ms |
| 展开、Toast 提示 | 240ms | 300–400ms |
| 大面积展开、重要通知 | 400ms | 450–600ms |
| 背景遮罩、全屏转场 | 700ms | 700–1000ms |

### 缓动曲线
- 进场用减速，出场用加速，全程都在屏幕上的元素用标准曲线：
  - Material 标准：`cubic-bezier(0.2, 0, 0, 1)`；强调进场：`cubic-bezier(0.05, 0.7, 0.1, 1)`；强调出场：`cubic-bezier(0.3, 0, 0.8, 0.15)`
  - Carbon 效率型（工具类界面）：标准 `cubic-bezier(0.2, 0, 0.38, 0.9)`，进场 `cubic-bezier(0, 0, 0.38, 0.9)`，出场 `cubic-bezier(0.2, 0, 1, 0.9)`
- Carbon 区分"效率型"（按钮、下拉、表格，克制）和"表现型"（打开新页面、主操作，偶尔用）。**工具软件以效率型为主**——AI 常把所有东西都做成弹跳、浮动的花哨动画。
- 必须支持"减少动态效果"（`prefers-reduced-motion`），不能只靠动画传达信息。（Carbon）

---

## 四、尺寸与布局

- **点击区域**：Apple 44×44pt、Material 48×48dp；WCAG 2.5.8 最低 24×24 CSS px（AAA 级 44×44）。图标可以小，可点区域不能小。
- **嵌套圆角要同心**：内层圆角 ≈ 外层圆角 − 内边距（内边距大于外圆角时，内层圆角为 0）。Apple 在 WWDC25 把同心圆角定为新设计语言的核心。AI 常犯：卡片 16px 圆角、里面按钮也 16px，看起来别扭。
- **按重要程度排序**，最重要的放上方和起始侧；用对齐和缩进表达从属关系；相关的东西靠近、无关的拉开。（Apple）
- **渐进披露**：一屏塞太多选项反而难用，次要功能收进菜单/折叠。（Apple）
- **macOS 窗口**：别把关键控件放窗口最底部（用户常把窗口拖到屏幕外一截）。（Apple）
- **空间变了功能不能变**：窄屏可以把侧边栏收成标签栏，但功能要一致。（Apple）

---

## 五、给 AI 的自检问题（从以上规则提炼）
1. 深色模式是不是只把背景改黑、文字改白？（应检查：字重、层级亮度、降饱和、图片、阴影）
2. 深色里有没有比背景更暗的卡片？有没有纯 #000 背景配纯 #FFF 大段文字？
3. 主色是不是满屏都在用？（应只用在 1–2 处）
4. 嵌套圆角同心了吗？
5. 数字列用等宽数字了吗？
6. 动画时长是不是一律 300ms ease？（应按面积分级、进出场用不同曲线）
7. 可点击区域够 44px 吗？
8. 有 hover / active / focus / disabled 四种状态吗？明暗下方向对吗？

---

## 出处
- Apple HIG – Dark Mode: https://developer.apple.com/design/human-interface-guidelines/dark-mode
- Apple HIG – Typography: https://developer.apple.com/design/human-interface-guidelines/typography
- Apple HIG – Layout: https://developer.apple.com/design/human-interface-guidelines/layout
- WWDC20 字体笔记: https://wwdcnotes.com/notes/wwdc20/10175
- Material Design – Dark theme: https://m2.material.io/design/color/dark-theme
- Material 深色主题解读: https://blog.prototypr.io/how-to-design-a-dark-theme-for-your-android-app-3daeb264637
- Material Motion tokens: https://github.com/material-components/material-components-android/blob/master/docs/theming/Motion.md
- IBM Carbon – Color: https://carbondesignsystem.com/elements/color/overview/
- IBM Carbon – Motion: https://carbondesignsystem.com/elements/motion/overview/
- Microsoft Fluent 2 – Elevation: https://fluent2.microsoft.design/elevation
- Ant Design – 暗色模式: https://ant.design/docs/spec/dark
- 光渗错觉与 GRAD 轴: https://nerdy.dev/adjust-perceived-typepace-weight-for-dark-mode-without-layout-shift
- 字体设计师讨论 White on black: https://typedrawers.com/discussion/comment/54288
- 同心圆角: https://nilcoalescing.com/blog/ConcentricRectangleInSwiftUI
- 点击区域: https://allaccessible.org/blog/wcag-258-target-size-minimum-implementation-guide
