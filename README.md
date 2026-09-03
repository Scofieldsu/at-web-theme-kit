# at-web-theme-kit

> **Web 前端「Linear 风格」主题设计规范与可复用资产库**
>
> 本套规范与资产从**企业级后台管理系统**的视觉重构实践中沉淀而来，与具体业务完全解耦：
> 不依赖任何业务代码，接入新系统即可获得一套一致的紧凑、扁平、现代配色。
>
> - 技术载体：Vue 3 + Ant Design Vue 4（`ConfigProvider` Design Token）+ CSS 变量（亮 / 暗双主题）
> - 代码形态：`theme/` 下 4 个文件，可直接整体复制到目标工程使用
> - 色板体系：主色 Indigo（Tailwind Indigo 500）+ 语义色（Radix Colors 9 号档）+ Zinc / Slate 灰阶

---

## 0. 一句话设计规则

> **Indigo `#6366f1` <span style="display:inline-block;width:12px;height:12px;border-radius:3px;background:#6366f1;vertical-align:middle;margin-left:2px"></span> 一个主色；Radix 四个语义色只以 12% 淡底出现；灰阶用 Zinc / Slate；字号 13px；圆角 4px；控件高度 32px；无阴影扁平；侧边栏 Slate-100 浅灰蓝；表头 `#fafafa` <span style="display:inline-block;width:12px;height:12px;border-radius:3px;background:#fafafa;border:1px solid rgba(0,0,0,0.15);vertical-align:middle;margin-left:2px"></span>。**

---

## 1. 设计基调

整体观感为**浅色紧凑的 Linear 风**，四个关键词：

1. **单一强调色**：Indigo 紫蓝是全系统唯一的强调色，链接、主按钮、激活态、聚焦光圈、选中行全部使用同一色系阶梯度；
2. **语义色只做淡底**：成功 / 警告 / 错误 / 信息四类状态色禁止大面积实色，统一采用「12% 同色透明底 + 同色文字 + 25~35% 同色细边框」的配方；
3. **扁平化**：卡片、按钮无阴影（或极浅阴影），小圆角（4px）、小字号（13px）、高信息密度；
4. **亮暗双主题**：全部颜色收敛为 CSS 变量，`html[data-theme]` 一键切换，深色下主色提亮一档、灰阶反转。

主题分三层实现，均收敛在少量资产文件中（见 §4 资产清单）：

| 层 | 资产文件 | 说明 |
|---|---|---|
| ① 组件级 Design Token | `theme/antd-theme-token.ts` | 喂给 antd `<ConfigProvider :theme>`，全局组件一次生效，业务代码零改动 |
| ② 全局 CSS 变量（亮 + 暗） | `theme/linear-components.css` | `--vben-*` 全量变量 + antd 组件全局覆盖 + 业务组件统一类 |
| ③ 业务语义 CSS 变量（亮 + 暗） | `theme/theme-vars.less` | `--bg-page/--bg-card/--text-*/--accent/--success/...` + `.theme-card` |
| ④ 侧边栏菜单专项 | `theme/menu-theme.less` | 浅色侧栏分层配色 + 激活态指示条 |

---

## 2. 配色体系（精确色值，色块即所见）

> 色块 `<span>` 为内联色样，若阅读器未渲染可对照 hex 值。

### 2.1 品牌主色 —— Indigo 阶梯度（唯一强调色）

| 用途 | 色值 | 色样 |
|---|---|---|
| 主色 primary | `#6366f1` | <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#6366f1;vertical-align:middle"></span> |
| hover | `#4f46e5` | <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#4f46e5;vertical-align:middle"></span> |
| active / pressed | `#4338ca` | <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#4338ca;vertical-align:middle"></span> |
| 主色淡底 | `rgba(99,102,241,0.08)` | <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:rgba(99,102,241,0.08);border:1px solid rgba(0,0,0,0.08);vertical-align:middle"></span> |
| 激活底 | `rgba(99,102,241,0.12)` | <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:rgba(99,102,241,0.12);border:1px solid rgba(0,0,0,0.08);vertical-align:middle"></span> |
| 聚焦光圈 | `rgba(99,102,241,0.10)` | <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:rgba(99,102,241,0.10);border:1px solid rgba(0,0,0,0.08);vertical-align:middle"></span> |

> 深色主题下主色整体提亮一档：主色 `#6d70f6` <span style="display:inline-block;width:12px;height:12px;border-radius:3px;background:#6d70f6;vertical-align:middle"></span>、hover `#7c7ffa` <span style="display:inline-block;width:12px;height:12px;border-radius:3px;background:#7c7ffa;vertical-align:middle"></span>、active `#5b5ef0` <span style="display:inline-block;width:12px;height:12px;border-radius:3px;background:#5b5ef0;vertical-align:middle"></span>、淡底 `rgba(109,112,246,0.15)`。

### 2.2 语义色 —— Radix Colors 9 号档

| 语义 | 亮色 | 深色 | 用途示例 |
|---|---|---|---|
| 成功 success | `#30a46c` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#30a46c;vertical-align:middle"></span> | `#3bb97e` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#3bb97e;vertical-align:middle"></span> | 通过、成功 |
| 警告 warning | `#f76b15` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#f76b15;vertical-align:middle"></span> | `#ff8c3a` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#ff8c3a;vertical-align:middle"></span> | 跳过、告警 |
| 错误 error | `#e5484d` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#e5484d;vertical-align:middle"></span> | `#f26a6f` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#f26a6f;vertical-align:middle"></span> | 失败、报错 |
| 信息 info | `#0090ff` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#0090ff;vertical-align:middle"></span> | `#1fa3ff` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#1fa3ff;vertical-align:middle"></span> | 提示、链接蓝 |
| 附加 purple | `#7c3aed` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#7c3aed;vertical-align:middle"></span> | 同亮色 | 特殊标记 |
| 附加 cyan | `#06b6d4` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#06b6d4;vertical-align:middle"></span> | 同亮色 | 次级目录 / 标签 |

**使用规则（重要）**：语义色不直接铺实色。Tag、状态徽标、区块标题、Alert 统一遵循
「`rgba(色, 0.12)` 淡底 + 语义色文字 + `rgba(色, 0.25~0.35)` 细边框」配方：

```css
.status-badge.passed { background: rgba(48, 164, 108, 0.12); color: #30a46c; border: 1px solid rgba(48, 164, 108, 0.35); }
.status-badge.failed { background: rgba(248, 113, 113, 0.12); color: #e5484d; border: 1px solid rgba(248, 113, 113, 0.25); }
.ant-tag-success     { background: rgba(48, 164, 108, 0.12);  color: #30a46c; }
```

### 2.3 中性色 —— 灰阶体系（Zinc / Slate 系）

| 层级 | 亮色 | 深色 |
|---|---|---|
| 主文字 | `#1c2024` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#1c2024;vertical-align:middle"></span> | `#e5e7eb` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#e5e7eb;border:1px solid rgba(0,0,0,0.15);vertical-align:middle"></span> |
| 次文字（label / 表头） | `#60646c` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#60646c;vertical-align:middle"></span> | `#9ca3af` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#9ca3af;vertical-align:middle"></span> |
| 辅助文字 / muted | `#9ca3af` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#9ca3af;vertical-align:middle"></span> | `#6b7280` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#6b7280;vertical-align:middle"></span> |
| 禁用文字 | `#d4d4d8` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#d4d4d8;border:1px solid rgba(0,0,0,0.15);vertical-align:middle"></span> | `#4b5563` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#4b5563;vertical-align:middle"></span> |
| 主边框 border | `#e5e5e5` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#e5e5e5;border:1px solid rgba(0,0,0,0.15);vertical-align:middle"></span> | `#2a2d38` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#2a2d38;vertical-align:middle"></span> |
| 输入框边框 border-input | `#d4d4d8` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#d4d4d8;border:1px solid rgba(0,0,0,0.15);vertical-align:middle"></span> | `#333745` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#333745;vertical-align:middle"></span> |
| 极浅边框 border-light | `#f0f0f0` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#f0f0f0;border:1px solid rgba(0,0,0,0.15);vertical-align:middle"></span> | `#202329` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#202329;vertical-align:middle"></span> |
| 默认按钮文字 | `#3f3f46` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#3f3f46;vertical-align:middle"></span> | — |

### 2.4 背景分层 —— 浅色下是「灰 - 白 - 浅灰」叠层

| 区域 | 亮色 | 深色 |
|---|---|---|
| 页面底色 | `#f8f9fa` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#f8f9fa;border:1px solid rgba(0,0,0,0.15);vertical-align:middle"></span> | `#0d0f13` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#0d0f13;vertical-align:middle"></span> |
| 内容区底色 | `#fafafa` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#fafafa;border:1px solid rgba(0,0,0,0.15);vertical-align:middle"></span> | 同页面底 |
| 卡片 / 内容 | `#ffffff` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#ffffff;border:1px solid rgba(0,0,0,0.15);vertical-align:middle"></span> | `#1e2028` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#1e2028;vertical-align:middle"></span> |
| 表头 / 弹窗头 / 次要卡片 | `#fafafa` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#fafafa;border:1px solid rgba(0,0,0,0.15);vertical-align:middle"></span> | `#262a34` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#262a34;vertical-align:middle"></span> |
| 顶部栏 | `#ffffff` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#ffffff;border:1px solid rgba(0,0,0,0.15);vertical-align:middle"></span> | `#1a1c23` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#1a1c23;vertical-align:middle"></span> |
| **侧边栏** | `#f1f5f9`（Slate 100） <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#f1f5f9;border:1px solid rgba(0,0,0,0.15);vertical-align:middle"></span> | `#16181e` <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#16181e;vertical-align:middle"></span> |
| 一级菜单块 | `#e2e8f0`（Slate 200） <span style="display:inline-block;width:14px;height:14px;border-radius:3px;background:#e2e8f0;border:1px solid rgba(0,0,0,0.15);vertical-align:middle"></span> | 随侧栏变量 |
| hover | `rgba(0,0,0,0.02~0.04)` | `rgba(255,255,255,0.05)` |

### 2.5 菜单激活态（唯一允许「紫」的区域）

侧边栏为**浅色**（Slate-100 底 + 1px `rgba(0,0,0,0.06)` 细右框）：

- 一级菜单：Slate-200 `#e2e8f0` <span style="display:inline-block;width:12px;height:12px;border-radius:3px;background:#e2e8f0;border:1px solid rgba(0,0,0,0.15);vertical-align:middle"></span> 色块，文字近黑 `#18181b`，字重 500、13px；
- 子菜单：文字中灰 `#71717a`（hover 加深 `#3f3f46`），hover 底 `rgba(0,0,0,0.04)`；
- **激活项 = `rgba(99,102,241,0.12)` 底 + `#6366f1` <span style="display:inline-block;width:12px;height:12px;border-radius:3px;background:#6366f1;vertical-align:middle"></span> 文字 + 左侧 2px 实色指示条**，图标同步变紫；
- 无圆角、无分隔线、项高 34px、子项缩进 36px。

### 2.6 品牌页 / 登录页特例（全系统唯一允许渐变与发光处）

深色背景 + 字符雨 / 粒子动效可选：

- 标题文字：`linear-gradient(135deg, #818cf8 0%, #6366f1 55%, #0090ff 100%)` 背景裁剪文字
  <span style="display:inline-block;width:12px;height:12px;border-radius:3px;background:#818cf8;vertical-align:middle"></span>→<span style="display:inline-block;width:12px;height:12px;border-radius:3px;background:#6366f1;vertical-align:middle"></span>→<span style="display:inline-block;width:12px;height:12px;border-radius:3px;background:#0090ff;vertical-align:middle"></span>
- 主按钮：`#818cf8 → #6366f1` 渐变 + `box-shadow: 0 0 20px rgba(99,102,241,0.35)` 外发光，hover 加深并提亮光晕；
- 输入框聚焦：`#6366f1` 边框 + `0 0 0 3px rgba(99,102,241,0.18)`。

---

## 3. 风格签名（非颜色的维度，接入时必须一并照搬）

| 维度 | 值 | 效果 |
|---|---|---|
| 基础字号 | **13px**（辅助 12px） | 比组件库默认 14px 更密 |
| 控件高度 | 32 / 38(lg) / 26(sm) / 22(xs) | 「扁按钮」，不臃肿 |
| 圆角 | **4px**（lg 6 / sm 2） | 方正中带一点柔 |
| 间距 | 12px 基准（lg 16 / sm 8 / xs 4） | 紧凑 |
| 阴影 | 卡片无阴影；全局极浅 `0 1px 2px rgba(0,0,0,0.03)`；下拉 `0 4px 12px rgba(0,0,0,0.08)` | 扁平贴页 |
| 表格 | 表头 `#fafafa` 底 + 500 字重 + `#1c2024` 字；行 padding 8×12；hover 极浅；无斑马纹 | 干净高密度 |
| 按钮 | 默认按钮边框 `#d4d4d8`、文字 `#3f3f46`、字重 500、无阴影 | 主次分明 |
| 弹窗 | 头 `#fafafa`，标题 14px / 600 | 层次感 |
| 标签 Tag | 无边框、12px、padding 2×8 | 轻量 |
| 滚动条 | 6px 极细、thumb `rgba(0,0,0,0.1)` | 细节克制 |
| 响应式 | ≤768px 字号 12 / 间距 8 / 控件 28，表格行更紧 | 小屏再紧凑一档 |
| 业务组件 | `status-badge`（✓/✗/⚠/– 前缀状态徽标）、`sec-title`（彩色淡底块标题）、`theme-card`（变量化卡片）、筛选栏统一间距 | 跨页观感一致 |

---

## 4. 资产清单与目录结构

```
at-web-theme-kit/
├── README.md                  # 本文档：设计规范 + 接入指南
└── theme/                     # 可直接整体复制到目标工程
    ├── antd-theme-token.ts    # ① 组件级 Design Token（antd ConfigProvider）
    ├── linear-components.css  # ② 全局 CSS 变量（亮/暗）+ antd 组件全局覆盖
    ├── theme-vars.less        # ③ 业务语义 CSS 变量（亮/暗）+ .theme-card
    └── menu-theme.less        # ④ 侧边栏浅色分层配色（@namespace 需换宿主前缀）
```

各文件职责与接入要点：

| 文件 | 内容 | 接入要点 |
|---|---|---|
| `antd-theme-token.ts` | `token`（主色/语义色/字号/控件高/圆角/间距/阴影）+ `components`（Table/Form/Button/Input/Card/Menu/Select/Modal/Tag 专项） | antd 系：直接作为 `<ConfigProvider :theme>` 的值；导出名为 `linearTheme` |
| `linear-components.css` | `:root` / `html[data-theme='dark']` 两组 `--vben-*` 变量 + 组件全局覆盖 + 业务统一类（status-badge / sec-title / tint-*） | 任意栈均可复用其变量段；覆盖段按组件库选择性搬用 |
| `theme-vars.less` | `--bg-page/--bg-card/--bg-sidebar/--text-*/--accent/--success/...` 亮暗两套 + `.theme-card` | 与 `linear-components.css` 语义对齐，供业务页面按用途取用 |
| `menu-theme.less` | 侧栏分层配色、激活态紫底 + 指示条、内容区底色 | 以 `@namespace: vben` 编译，换宿主工程时把前缀改为自己的 CSS 前缀 |

---

## 5. 接入步骤（新系统如何配色一致）

### 5.1 任何技术栈都要做的：先建一份 CSS 变量

把 §2.3 / §2.4 的亮、暗两套色板原样拷贝成 `:root` 与 `[data-theme='dark']` 两组变量
（可直接复用 `linear-components.css` 顶部的变量段，变量名按习惯改 `--accent` / `--bg-*` / `--text-*` 亦可），
尺寸变量 `--radius` / `--control-h` / `--space` 一并带上。

**铁律：业务页面只准引用变量，禁止硬编码色值** —— 硬编码是后续主题切换失效与「旧色值覆盖补丁」的根源。

### 5.2 按组件库落地

1. **使用 antd / ant-design-vue 4**：把 `theme/antd-theme-token.ts` 整体放进
   `<ConfigProvider :theme="linearTheme">`，所有组件一次变样、业务代码零改动。
   深色切换：`isDark` 时在 `linearTheme` 上 `Object.assign` 一层深色 token 覆盖。
2. **使用 Element Plus / Naive UI / 其他组件库**：用 CSS 变量逐类覆盖组件样式 —— 对照
   `linear-components.css` 中 Table / Button / Input / Select / Modal / Tag / Alert 的写法
   （13px、32px 高、4px 圆角、无阴影、12% 淡底色块、hover / focus 变主色），在新组件库等价重写一份。
3. **侧边栏**：按 `theme/menu-theme.less` 的层级配方（Slate-100 底 / Slate-200 一级块 / 中灰子项 /
   激活 = 12% 紫底 + `#6366f1` 字 + 2px 左指示条），把 `@namespace` 换成宿主 CSS 前缀。
4. **业务组件三件套原样保留**：`status-badge`（✓/✗/⚠/– 状态徽标）、`sec-title`（彩色淡底块标题）、
   `theme-card`（变量化卡片）—— 这是跨页面观感统一的关键，直接从 `linear-components.css` 抄取。
5. **深色主题**：变量已备好（§2 各表「深色」列），做成 toggle 切换 `html[data-theme]` 即可；
   主色提亮一档、文字转 `#e5e7eb` 系、背景降为近黑蓝灰 `#0d0f13`。
6. **品牌识别**：登录/品牌页的 Indigo 渐变标题 + 发光按钮可保留为记忆点；除此之外保持
   「只有 Indigo 一种强调色、语义色只以 12% 淡底出现」，配色就不会漂移。

### 5.3 落地自检清单

- [ ] `:root` / `[data-theme='dark']` 两组变量就位，业务页面无硬编码色值
- [ ] 主色 `#6366f1` <span style="display:inline-block;width:12px;height:12px;border-radius:3px;background:#6366f1;vertical-align:middle"></span>（hover `#4f46e5` / active `#4338ca`），全系统无第二强调色
- [ ] 表格：表头 `#fafafa` <span style="display:inline-block;width:12px;height:12px;border-radius:3px;background:#fafafa;border:1px solid rgba(0,0,0,0.15);vertical-align:middle"></span>、行 padding 8×12、hover 极浅、无斑马纹
- [ ] 按钮 / 输入框 / Select 统一 32px 高、4px 圆角、13px 字、聚焦光圈主色 10%
- [ ] Tag / 徽标 / Alert 全部 12% 淡底 + 语义色文字 + 细边框
- [ ] 卡片无阴影、12~16px 内边距、标题 14px / 600
- [ ] 侧边栏 Slate-100、激活态 2px Indigo 指示条
- [ ] 深色主题可一键切换且主色提亮一档

---

## 6. 日常调整入口

| 想改什么 | 改哪里 |
|---|---|
| 主色 / 语义色 / 字号 / 控件高 / 圆角 / 间距 / 阴影 | `theme/antd-theme-token.ts` 的 `token`（antd 场景）；同步改 `linear-components.css` 顶部变量（CSS 场景） |
| 表格 / 表单 / 按钮 / 卡片等组件细节 | `theme/antd-theme-token.ts` 的 `components`（antd 场景）或 `linear-components.css` 对应覆盖段 |
| 深色主题表现 | `linear-components.css` / `theme-vars.less` 中 `html[data-theme='dark']` 一段 |
| 侧边栏菜单 | `theme/menu-theme.less` |
| 业务语义变量 | `theme/theme-vars.less` 亮暗两套 |

> 调整技巧：一次只改一处 → 刷新 → 看效果 → 再改下一处；不确定时先在浏览器 DevTools 里用
> `document.documentElement.style.setProperty('--vben-primary', '...')` 试效果，满意后再落回文件。

---

*一句话收尾：Indigo `#6366f1` <span style="display:inline-block;width:12px;height:12px;border-radius:3px;background:#6366f1;vertical-align:middle"></span> 一个主色、Radix 四语义色只做淡底、灰阶用 Zinc/Slate、字号 13、圆角 4、控件 32、无阴影、侧栏 Slate-100、表头 `#fafafa` <span style="display:inline-block;width:12px;height:12px;border-radius:3px;background:#fafafa;border:1px solid rgba(0,0,0,0.15);vertical-align:middle"></span>。*


```
