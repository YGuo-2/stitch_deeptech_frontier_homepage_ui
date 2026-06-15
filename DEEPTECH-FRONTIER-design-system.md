# DEEPTECH FRONTIER · 深蓝前沿 — 设计规范

> **版本** v1.0 · **更新日期** 2026/06/15
> **定位**:沉浸式前沿科技品牌站(首页 + 4 子页),用 Google Stitch 生成。
> **一句话定调**:瑞士国际主义 × 高端设计刊物。**审美来自网格、留白与字体本身,而非特效。克制即减法。**

---

## 目录

0. [设计哲学](#0-设计哲学)
1. [品牌与信息架构](#1-品牌与信息架构)
2. [版面网格系统](#2-版面网格系统)
3. [色彩系统](#3-色彩系统)
4. [字体系统](#4-字体系统)
5. [间距系统](#5-间距系统)
6. [组件规范](#6-组件规范)
7. [全局禁止清单](#7-全局禁止清单)
8. [插图规范 STYLE LOCK](#8-插图规范-style-lock)
9. [页面蓝图(逐页)](#9-页面蓝图逐页)
10. [Stitch 工作流与话术](#10-stitch-工作流与话术)
11. [常见翻车点与修复话术](#11-常见翻车点与修复话术)
12. [附录 · 一键复用片段](#12-附录--一键复用片段)

---

## 0. 设计哲学

### 三条核心原则

1. **克制即减法**。高级感来自拿掉东西,不是堆东西。每加一个元素都要问"删掉它会更好吗"。
2. **网格与字体说话**。版面的张力靠尺度对比、对齐、留白来制造,而不是靠特效、光效、装饰图形。
3. **像一本科技刊物,不像一个科幻游戏 UI**。参照系是高端设计杂志 / 实验室年报 / Apple·Linear·Vercel,而不是赛博朋克 HUD。

### 反对什么(理念层)

本项目诞生于对"AI 烂大街科技风"的明确排斥。以下是被永久拉黑的俗套,理解它们**为什么俗**比记住清单更重要:

- **大面积蓝 / 蓝黑背景** —— 所有 AI 生成"科技站"的最大公约数,一眼廉价。真正高级的科技品牌几乎从不靠蓝底传达科技感。
- **元素堆砌** —— 网格 + 线路 + 光轨 + 参数标签 + 光点一股脑堆上,嘴上"克制"手上"满屏"。廉价感正源于此。
- **发光晶体芯片 / AI 核心 + 环形数据轨道 + HUD 读数** —— Midjourney 科幻图最烂大街的一套,毫无品牌个性。
- **形容词驱动**(冷静/克制/精密/未来感) —— AI 对这些词早已脱敏,它们不产生任何真实视觉约束。

> **设计准则**:不因为主题里有"蓝"字,就用蓝。约束要落到**具体的色值、尺寸、网格、材质**上,而非形容词。

---

## 1. 品牌与信息架构

### 品牌锁定

| 项 | 值 |
|---|---|
| 中文名 | 深蓝前沿 |
| 英文辅助标识 | DEEPTECH FRONTIER |
| Wordmark 锁定 | 中文 18px 墨黑 + 英文 11px 大写灰(字距放大) |

> **关于名字里的"蓝"**:「深蓝」在本系统中是 **墨色与克制的代名词,不是背景主色**。蓝(冷青)只作点睛,全页面积 < 5%。这条是整套设计的题眼。

### 站点导航

```
首页 · 技术矩阵 · 探索前沿 · 创新成果 · 未来计划
```
当前项以 2px 冷青下划线标识(全页极少数用色处之一)。

### 内容清单(信息架构参考)

**九大技术领域**(技术矩阵页):
人工智能 · 量子计算 · 深空探索 · 未来能源 · 智能制造 · 新材料 · 脑机接口 · 合成生物 · 空间计算

**领域代码**(状态日志 / 分布条用,mono):
`GEN-AI` · `NEUROLINK` · `ORBITAL` · `HELION` · `LITHIUM+` · `SYN-BIO` · `SPACE-C` · `QUANTUM` · `AGENT-S`

**代表案例**(创新成果页):
- 量子干涉矩阵优化(QUANTUM)
- 全自动黑灯工厂 2.0(MANUFACTURING)

**专题**(探索前沿页):
- 相干性的边界:从量子纠缠到通用计算的跨越

---

## 2. 版面网格系统

| 参数 | 值 |
|---|---|
| 画布宽度 | 1440px(桌面端基准) |
| 栏数 | 12 栏 |
| 左右边距 | 96px |
| 栏间距(gutter) | 24px |
| 内容最大宽度 | 1248px(1440 − 2×96) |

**规则**
- **✓ 应**:所有元素严格对齐到 12 栏与共享基线;大量负空间;非对称布局优先于居中。
- **✗ 忌**:均匀铺满、每个区块等高等宽(那是表格不是版面)。
- **节奏**:相邻区块之间必须有**尺度或留白的变化**,避免连续同节奏堆叠。

---

## 3. 色彩系统

### 调色板(严格遵守占比)

| 角色 | HEX | RGB | 占比 | 用途 |
|---|---|---|---|---|
| 背景 暖纸白 | `#F6F5F1` | 246,245,241 | 90%+ | 全站底色。**禁止任何蓝色背景** |
| 墨黑 | `#0B0B0C` | 11,11,12 | — | 主文字、标题、关键数字 |
| 次级灰 | `#6F6F74` | 111,111,116 | — | 说明文字、元数据、英文标签 |
| 发丝线 | `#E3E1DB` | 227,225,219 | — | 1px 分割线、边框、表格行线 |
| 强调 冷青 | `#16B9A6` | 22,185,166 | **< 5%** | 仅点睛(见白名单) |
| 图版背景 | `#ECEBE7` | 236,235,231 | — | 插图棚拍扫光背景(比纸白略冷) |

### 冷青 `#16B9A6` 使用白名单

冷青是手术刀,不是油漆桶。**只允许**出现在:
1. 当前导航项下的 2px 下划线
2. 链接 / 行的 hover 态
3. 索引小圆点、状态点(单个激活点)
4. 一条贯穿性的细规线(eyebrow 标签尾随的短线)
5. 数据分布条中**单个**最高亮段

- **✗ 忌**:用作填充、背景、大色块、柱状图成对上色、整行高亮。

### Do / Don't

- **✓ 应**:近乎黑白灰的画面里,冷青一闪即过,克制到几乎要找一下才看见。
- **✗ 忌**:蓝/青占比超过 5%;出现第二个强调色;用渐变 mesh 光斑。

### 暗色"夜间刊"变体(预留)

如需暗色态:暖纸白 → 暖炭黑(非蓝黑),冷青略提亮,其余 token 与规则不变。**严禁退回"蓝黑科技"俗套**。

---

## 4. 字体系统

### 字体族

| 用途 | 字体方向 |
|---|---|
| 显示 / 标题 / 正文 | 无衬线 grotesque(Suisse Int'l / Söhne / Helvetica Now Display 气质) |
| 数字 / 元数据 / 代码 | 等宽 mono(ABC Diatype Mono / Söhne Mono 气质) |

### Type Scale

| 层级 | 字号 | 字重 | 字距 | 行高 | 用途 |
|---|---|---|---|---|---|
| Display XL | 140px | 650 | -0.02em | 1.0 | 首页 hero 中文主标题 |
| Display L | 96px | 650 | -0.02em | 1.05 | 子页 masthead 中文标题 |
| Headline | 40px | 600 | -0.01em | 1.1 | featured 专题标题 |
| Title | 28–32px | 600 | 0 | 1.2 | 案例名 / 领域名 / thesis 句 |
| Subtitle | 22px | 600 | 0 | 1.3 | 中文小标 |
| Body L | 18px | 400 | 0 | 1.6 | 首屏简介 |
| Body | 16px | 400 | 0 | 1.6 | 正文 / 说明 |
| Label(caps) | 11px | 500 | +0.18em | 1.4 | 英文大写标签 / kicker |
| Nav | 14px | 500 | 0 | — | 导航项 |
| Mono Meta | 12–13px | 400 | 0 | 1.5 | 索引 / 坐标 / 读数 / 百分比 |

### 规则

- **数字一律 mono**:索引(01–09)、百分比(88%)、坐标、指标、年份、读数。
- **英文标签一律大写 + 放字距**(+0.18em),用作 eyebrow / kicker / 分类标签。
- **中英文混排**:中文用 grotesque 主字重,英文辅助标识小一号、大写、灰、放字距,作"副标"压在中文下方或右侧。
- **✗ 忌**:中文用衬体充当"科技感"、标题用斜体、正文字号 < 14px。

---

## 5. 间距系统

以 8px 为基准的间距刻度,所有 padding / margin 取自此表:

```
4 · 8 · 16 · 24 · 32 · 48 · 64 · 96 · 128
```

- 组件内边距:最小 24px;featured 区块 48–64px。
- 区块之间(masthead → 主体 → 次级区):96–128px,**用留白制造呼吸**。
- 顶部导航高度 ≈ 72–80px,下方紧跟 1px 发丝线。

---

## 6. 组件规范

> 贯穿全部组件的两条铁律:**只用 1px 发丝线,绝不用卡片**(无边框框 / 无阴影 / 无填充色块);**用文字链接,不用实心按钮**。

### 6.1 顶部导航

- 结构:左 Wordmark(中文 18px 墨黑 + 英文 11px 大写灰),右导航 5 项(14px,间距宽松),最右可选 `SUBSCRIBE` 描边小按钮。
- 下边界:一条 1px 发丝线 `#E3E1DB`。
- 当前项:下方 2px 冷青下划线。
- 玻璃/半透明:**不用**。轻薄即可,纸白实底。

### 6.2 文字链接 / CTA(取代按钮)

- 主 CTA:墨黑文字 + 下划线 + `→`(例:`进入技术矩阵 →`)。
- 次 CTA:次级灰文字,无下划线。
- **✗ 忌**:实心填充按钮、圆角胶囊、投影按钮。

### 6.3 发丝线与分隔(取代卡片)

- 所有"区块感"由 1px 发丝线 `#E3E1DB` 划分,而非卡片。
- featured 大区块靠**尺度 + 留白**界定,不靠边框。
- **✗ 忌**:`border-radius` 卡片、`box-shadow`、玻璃拟态、填充底色块。

### 6.4 数据表格

- 仅用横向发丝线分隔行,无竖线、无斑马纹、无外框。
- 数字右对齐,mono。
- 状态用小写 caps + 单个状态点(激活点冷青)。
- 行 hover:序号 / 关键数字变冷青。
- **✗ 忌**:`[SCALING]` 这类方括号标签堆砌(保留纯 mono 数字 + 一词状态即可)、整块加边框变成"小部件"。

### 6.5 图版(图片容器)

- 容器:图片 + 上下 1px 发丝线框定,**不放进卡片**。
- 图注:下方一行 mono(例:`FIG.01 — CORE SYSTEM ／ 41.8902° N`)。
- 图片本身:严格遵循 [STYLE LOCK](#8-插图规范-style-lock)。
- **✗ 忌**:圆角图、带阴影浮起的图、图上叠加 HUD/文字/URL。

### 6.6 索引、编号与标签

- 编号:mono `01`–`09`,常配一个冷青小圆点。
- eyebrow:mono 大写一行 + 尾随一条短冷青发丝线(例:`TECHNOLOGY MATRIX — 09 DOMAINS / INDEX 2026 ——`)。
- 分类标签:11px 大写放字距,次级灰(例:`QUANTUM` / `AI` / `MANUFACTURING`)。

### 6.7 状态点 / 成熟度 / 向量

- 成熟度:5 点刻度 `●●●○○`(实心=已达),灰色;**不上冷青**(避免泛蓝)。
- 向量:mono 箭头 `↑ ↗ → `+ 单词(`EXPEND` / `ACCEL` / `STABLE`)。
- 状态:`ACTIVE` / `RESEARCH` / `SCALING`,小写 caps,激活点冷青。

### 6.8 页脚

- 左:Wordmark + 版权行(mono,次级灰)。
- 右:分组链接(INDEX / LEGAL 等),11px,下划线。
- 上边界:可选一条发丝线。背景仍纸白。

---

## 7. 全局禁止清单

整个项目的"反俗套护栏"。任何页面、任何改动都不得引入:

```
✗ 大面积蓝 / 蓝黑背景
✗ 玻璃拟态(glassmorphism)卡片
✗ 发光晶体芯片 / AI 核心装置
✗ 环形 / 轨道数据图形
✗ HUD 参数读数面板
✗ 漂浮光点 / 粒子
✗ 渐变 mesh 光斑 / blob
✗ 霓虹描边 / 发光描边
✗ 假元数据 cosplay(SECURITY_LEVEL: HIGH_ALPHA / ENCODING: BINARY_STREAM 等)
✗ 廉价科幻特效
✗ CGI 渲染感插图(要实物摄影)
✗ 卡片边框 / 阴影 / 圆角胶囊按钮
```

---

## 8. 插图规范 STYLE LOCK

全站插图共享一套**摄影 DNA**,只换主体不换气质——这是统一感的来源。锚点图为首页的「晶格立方体」。

### 8.1 摄影 DNA

| 要素 | 值 |
|---|---|
| 媒介 | 棚拍微距**实物摄影** —— 非渲染、非插画、非 CGI |
| 材质 | 拉丝铝 + 透明玻璃 / 亚克力 |
| 色彩 | 近灰度,冷中性银灰,几乎无饱和,玻璃内仅一丝冷调 |
| 光 | 柔和漫射棚光,平缓影调,自然软阴影 |
| 背景 | 无缝浅灰扫光 `#ECEBE7`,大量空白 |
| 景深 | 浅景深,近端锐利、向后柔化 |
| 构图 | 主体从画面一侧切入,留白充足 |
| 气质 | 冷静、临床精密、美术馆级 |

### 8.2 可粘贴块(每次出图原样使用)

```
[STYLE LOCK]
Studio macro product photograph — NOT a render, NOT illustration, NOT CGI.
A precision-engineered abstract object in brushed aluminum and clear glass / acrylic.
Monochrome, near-grayscale: cool neutral silver-grays, desaturated, only the faintest cool
tint inside the glass — no saturated color. Soft diffused studio light, gentle tonal
gradients, soft natural shadows. Seamless soft light-gray background sweep (#ECEBE7),
generous empty negative space. Shallow depth of field — sharp on the nearest edge, falling
gently out of focus. Calm, clinical, museum-grade. High-resolution photographic realism.
```

### 8.3 Negative(防翻车)

```
Negative: saturated color, blue or dark background, neon, glow, lens flare, HUD,
floating particles, busy background, CGI-render look, fake reflections,
any text or URL overlaid on the image.
```

### 8.4 各页插图主体(只换这一行 `SUBJECT`)

```
首页(锚点):  a modular 3D lattice cube — brushed-aluminum struts framing rows of clear
              glass cells. 所有其他图向它看齐。

技术矩阵:     人工智能 → a glass-and-aluminum neural lattice
              量子计算 → mirrored optical glass prisms refracting light

探索前沿:     a pair of mirrored clear glass prisms in aluminum mounts, quietly refracting
              soft light between them(相干 / 纠缠)

创新成果:     CASE 01 量子干涉 → a grid/matrix of clear optical glass prisms,光的折射
                                 (玻璃为主、网格)
              CASE 02 黑灯工厂 → a linear array of identical machined aluminum modules
                                 receding in a row(金属为主、线列)

未来计划:     a row of identical aluminum-and-glass modules receding into shallow depth,
              evenly spaced(序列 / 进程)
```

### 8.5 后期与配图原则

- **照片保持近灰度**;那层"冷青 duotone"由设计系统(发丝线框 + mono 图注)去加,**别让照片自带蓝**,守住冷青 < 5%。
- **同一物种**(模块化几何 + 金属玻璃)→ 天然成系列;一玻璃一金属、一网格一线列,放一起就不会撞脸。
- **全站图版总数控制在 4–5 张**,过多会破坏"克制"的整体气质。
- **实物感优先**:若出图发假像 CGI,把 `Studio macro product photograph` 提到最前并追加 `real photograph, shot on a macro lens`。

---

## 9. 页面蓝图(逐页)

> 五页共享设计系统,但**各有版式骨架**,避免千篇一律。

### 9.1 首页 Homepage

- **骨架**:非对称英雄区(左排版 / 右图版)+ 首屏下方露出编辑式模块索引。
- **Hero 左 7 栏**:mono eyebrow + 冷青细线 → Display XL「深蓝前沿」(~140px) → 英文 kicker → 两行简介 → 两个文字链接 CTA。
- **Hero 右 5 栏**:STYLE LOCK 晶格图版,1px 发丝线框 + mono 图注 `FIG.01`。
- **模块索引**:四大板块(技术矩阵 / 深空探索 / 智能制造 / 未来能源)以发丝线分隔,栏宽不等,mono 序号 + 冷青小圆点。
- **✗ 忌**:右侧出现发光芯片/数据轨道/HUD。

### 9.2 技术矩阵 Technology Matrix

- **骨架**:**非对称** featured matrix(2 大格带图 + 7 小格)→ 一句 thesis 留白停顿 → 成熟度分布条 → 页脚。
- **Masthead**:mono eyebrow + Display L「技术矩阵」+ 两行简介。
- **核心 · featured matrix**:
  - 2 个 flagship 领域(人工智能、量子计算)= 大 feature 格(各跨 ~6 栏、更高),含 STYLE LOCK 图 + 大 mono 成熟度数字 + 领域名 + 一行说明。
  - 其余 7 领域 = 紧凑文字格(序号 + 名 + 成熟度点 + 向量),每行 3 个。
  - 大小格的**尺度跳跃**就是看点;仅发丝线分隔,无卡片。
- **thesis 停顿**:一句 ~32px grotesque 主张 + mono 署名,四周大留白(一处呼吸,不是更多数据)。
- **成熟度分布条**:一条全宽横条分 9 段,灰度填充,**仅最高一段冷青**,下方 mono 领域代码;无外框。
- **✗ 忌**:连续三个同节奏数据块;底部出现带边框的"SYSTEM ARCHITECTURE VISUALIZATION"柱状图小部件。

### 9.3 探索前沿 The Frontier

- **骨架**:大专题(左图右文)+ 文章索引流。
- **Masthead**:mono eyebrow + Display L「探索前沿」+ 一行简介。
- **Featured 专题**:左 7 栏 STYLE LOCK 图版(双棱镜,呼应"纠缠/相干")+ 发丝线框 + `FIG.01 — FEATURED`;右 5 栏 mono kicker(`QUANTUM / 量子计算`)+ Headline 标题 + 两行导语 + mono 署名行(日期 · 阅读时长 · 阅读全文 →)。
- **文章索引**:两栏流,6 条,发丝线分隔;每条 mono 日期 + 分类标签 + 中文标题 + 一行摘要;hover 日期变冷青;多数纯文字、少数带小图版。
- **✗ 忌**:图位留空只剩裸露图片 URL(见 §11)。

### 9.4 创新成果 Innovations

- **骨架**:带 mono 大数字指标的案例索引 + 2 个 featured 案例。
- **Masthead**:mono eyebrow(`SELECTED WORKS 2019–2026 · 24 PROJECTS`)+ Display L「创新成果」+ 一行简介。
- **案例索引行**:6 行,发丝线分隔,跨全栏;左 mono 序号 + 年份,中 项目名(Title)+ 分类标签,右 一个 mono 大数字指标(`99.8%` / `×12` / `0.4ms`)+ 小灰单位;hover 整行序号 + 指标变冷青。
- **2 个 featured 案例**:配 STYLE LOCK 图版,**两张必须明显不同** —— CASE 01 玻璃 + 网格,CASE 02 金属 + 线列;发丝线框,非卡片。
- **✗ 忌**:两张案例图用同一堆"金属叠片"、图与标题不符。

### 9.5 未来计划 Roadmap

- **骨架**:horizon 概览条 + 纵向时间轴年表。
- **Masthead**:mono eyebrow(`ROADMAP — 2026 ▸ 2040`)+ Display L「未来计划」+ 一行简介。
- **Horizon 条**:一条横向发丝线 + mono 刻度 `NOW · 2030 · 2035 · 2040`,`NOW` 刻度冷青小标记。
- **纵向时间轴**:左侧一条发丝竖线为脊,冷青节点小圆点;每个里程碑 = 左栏大 mono 年份 + 右侧阶段名(Title)+ 英文小标 + 两行说明 + mono 状态标签(`IN PROGRESS` / `PLANNED` / `EXPLORATORY`,激活点冷青);里程碑间大留白。
- **✗ 忌**:把节点做成填充色块/卡片。

---

## 10. Stitch 工作流与话术

### 10.1 生成顺序

在同一个 Stitch thread 内,按 首页 → 技术矩阵 → 探索前沿 → 创新成果 → 未来计划 顺序生成,让五页字体/灰阶/间距继承一致。

### 10.2 新建页面 · 开头永远先锚定

```
Inherit the DEEPTECH FRONTIER design system: Swiss editorial, paper-white #F6F5F1
(NO blue fields), ink #0B0B0C, secondary gray #6F6F74, 1px hairlines #E3E1DB ONLY
(no cards / borders / shadows), cold-cyan #16B9A6 accent <5% (active nav / dots / hover /
one rule only), grotesque display + mono numerals, 12-col grid / 96px margins.
Same thin top nav + footer. Images use the [STYLE LOCK] treatment, hairline-framed.
Forbidden: blue/blue-black backgrounds, glassmorphism, glowing chips, orbital/HUD graphics,
floating particles, neon, gradient blobs, fake security/binary metadata, CGI-render look.
```

### 10.3 生成 / 替换插图

```
Replace the illustration on the [页面] page. Use EXACTLY the [STYLE LOCK] treatment so it
matches the homepage lattice image. Frame it with 1px hairlines and keep its mono caption —
NOT in a bordered card. Subject: [§8.4 对应那一行]. Do not use an external image URL —
generate the illustration inline. No text or URL overlaid on the image.
```

### 10.4 改版 / 局部修改

- 永远以「Inherit the design system…」开头,再描述改动。
- 改动只动**核心区**,锁定句:`Everything else on the page stays unchanged.`
- 涉及尺度/版式时强调:`feature cells are defined by hairlines and scale only — no border, no fill, no shadow.`

---

## 11. 常见翻车点与修复话术

实战中反复出现的问题与对应修复(可直接复制改动指令):

### 11.1 冒出带边框的"数据可视化"小部件(柱状图框)

- **症状**:底部出现实心边框 + 无意义柱状图 + `SECURITY_LEVEL / FRAME_ID` 假元数据,成对青柱破坏占比。
- **修复**:删除整块,替换为发丝线分布条,或直接删掉(克制即减法)。
```
Remove the bordered "SYSTEM ARCHITECTURE VISUALIZATION" box and ALL its corner metadata
(LAST_SYNC, SECURITY_LEVEL, FRAME_ID, ENCODING, COORDS). It is a hard-bordered card with a
meaningless chart and fake HUD metadata — all forbidden. Replace with a flat hairline
"MATURITY DISTRIBUTION" bar (gray segments, only one cyan segment, no border), or remove it.
```

### 11.2 图位留空,裸露图片 URL

- **症状**:图没渲染,只剩 `lh3.googleusercontent.com/...` 当文字显示。
- **修复**:清掉 URL,内联生成,并加 negative。
```
Remove the broken image URL text completely and generate the illustration inline using the
[STYLE LOCK]. Do not use an external image URL. Negative: any text or URL overlaid on image.
```

### 11.3 插图与内容不符 / 两图撞脸

- **症状**:量子专题配金属叠片;两个案例用同一堆图。
- **修复**:主体对位 + 强制差异化。
```
Give each illustration a subject matched to its headline (see §8.4), and make the two look
clearly different — one glass-and-grid, one metal-and-row. Same [STYLE LOCK] treatment.
```

### 11.4 页面太单调(全是数据列举)

- **症状**:连续多个同节奏数据块,无图、无尺度对比。
- **修复**:用编辑节奏破解(尺度对比 + 一张英雄图 + 留白停顿),**不加装饰**。
```
Fix monotony through editorial rhythm ONLY — promote 1–2 items to large feature cells with a
[STYLE LOCK] image, keep the rest compact, arrange asymmetrically (hairlines only), and add
one breathing beat (a single large thesis line with whitespace). No decoration, no color.
```

### 11.5 玻璃卡片 / 边框复发

- **修复**:`All blocks are defined by 1px hairlines and scale only — no border, no fill, no shadow, no glassmorphism.`

---

## 12. 附录 · 一键复用片段

**配色速查**
```
纸白 #F6F5F1 · 墨黑 #0B0B0C · 次级灰 #6F6F74 · 发丝线 #E3E1DB · 冷青 #16B9A6(<5%) · 图版底 #ECEBE7
```

**设计系统继承句**(每次新页/改动开头) → 见 §10.2
**STYLE LOCK 出图块** → 见 §8.2 + §8.3 Negative
**各页插图主体** → 见 §8.4
**修复话术合集** → 见 §11

---

### 变更记录

| 版本 | 日期 | 说明 |
|---|---|---|
| v1.0 | 2026/06/15 | 初始版。沉淀设计系统、STYLE LOCK 插图规范、五页蓝图、Stitch 话术与实战修复。 |

---

*本规范服务于「深蓝前沿 / DEEPTECH FRONTIER」。核心信条一句话:**克制即减法,网格与字体说话,蓝是点睛不是底色。***
