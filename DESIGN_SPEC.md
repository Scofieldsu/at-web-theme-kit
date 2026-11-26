# Linear 风格设计系统完整清单

> 基于 rpa-test-automation/web-vben 项目提取的完整设计系统规范  
> 适用于 at-web-theme-kit 主题包

---

## 📋 目录

1. [色彩系统](#色彩系统)
2. [字体系统](#字体系统)
3. [间距系统](#间距系统)
4. [圆角系统](#圆角系统)
5. [尺寸系统](#尺寸系统)
6. [阴影系统](#阴影系统)
7. [组件样式规范](#组件样式规范)
8. [菜单样式规范](#菜单样式规范)
9. [业务组件样式](#业务组件样式)
10. [响应式断点](#响应式断点)
11. [过渡动画](#过渡动画)

---

## 色彩系统

### 🎨 主题色（Primary）

基于 **Indigo** 色系（Linear 标志性颜色）

#### 亮色主题
| 变量名 | 色值 | 用途 | 示例 |
|--------|------|------|------|
| `--vben-primary` | `#6366f1` | Indigo 500，主色 | 主按钮、链接、激活状态 |
| `--vben-primary-hover` | `#4f46e5` | Indigo 600，悬停 | 按钮 hover |
| `--vben-primary-active` | `#4338ca` | Indigo 700，按下 | 按钮 active |
| `--vben-primary-bg` | `rgba(99, 102, 241, 0.08)` | 半透明背景 | 次要按钮背景、高亮背景 |
| `--accent` | `#6366f1` | 兼容旧变量 | 同 primary |

#### 暗色主题
| 变量名 | 色值 | 用途 |
|--------|------|------|
| `--vben-primary` | `#6d70f6` | 深色下主色（稍微亮一点） |
| `--vben-primary-hover` | `#7c7ffa` | 深色 hover |
| `--vben-primary-active` | `#5b5ef0` | 深色 active |
| `--vben-primary-bg` | `rgba(109, 112, 246, 0.15)` | 深色半透明背景 |

---

### 🎯 语义色（Semantic Colors）

基于 **Radix UI** 色板

#### 亮色主题
| 类型 | 变量名 | 色值 | 色系来源 |
|------|--------|------|----------|
| **成功** | `--vben-success` | `#30a46c` | Radix Green 9 |
| **警告** | `--vben-warning` | `#f76b15` | Radix Orange 9 |
| **错误** | `--vben-error` | `#e5484d` | Radix Red 9 |
| **信息** | `--vben-info` | `#0090ff` | Radix Blue 9 |

#### 暗色主题
| 类型 | 变量名 | 色值 | 说明 |
|------|--------|------|------|
| **成功** | `--vben-success` | `#3bb97e` | 比亮色稍亮 |
| **警告** | `--vben-warning` | `#ff8c3a` | 比亮色稍亮 |
| **错误** | `--vben-error` | `#f26a6f` | 比亮色稍亮 |
| **信息** | `--vben-info` | `#1fa3ff` | 比亮色稍亮 |

---

### 📝 文字色（Text Colors）

#### 亮色主题
| 变量名 | 色值 | 用途 | 对比度 |
|--------|------|------|--------|
| `--vben-text-primary` | `#1c2024` | 主文字（深灰黑） | AAA |
| `--vben-text-secondary` | `#60646c` | 次要文字（中灰） | AA |
| `--vben-text-tertiary` / `--text-muted` | `#9ca3af` | 辅助文字（浅灰） | AA |
| `--vben-text-disabled` | `#d4d4d8` | 禁用文字 | - |

#### 暗色主题
| 变量名 | 色值 | 用途 |
|--------|------|------|
| `--vben-text-primary` | `#e5e7eb` | 深色主文字 |
| `--vben-text-secondary` | `#9ca3af` | 深色次要文字 |
| `--vben-text-tertiary` | `#6b7280` | 深色辅助文字 |
| `--vben-text-disabled` | `#4b5563` | 深色禁用文字 |

---

### 🎭 背景色（Background Colors）

#### 亮色主题
| 变量名 | 色值 | 用途 |
|--------|------|------|
| `--vben-bg-base` / `--bg-card` | `#ffffff` | 基础背景（卡片、输入框） |
| `--vben-bg-elevated` / `--bg-card-alt` | `#fafafa` | 抬升背景（表头、卡片头部） |
| `--bg-page` | `#f8f9fa` | 页面底色（比纯白暖一点） |
| `--bg-sidebar` | `#f1f5f9` | 侧边栏浅色（Slate 100 蓝灰） |
| `--vben-bg-hover` / `--bg-hover` | `rgba(0, 0, 0, 0.02)` | Hover 半透明 |
| `--vben-bg-active` / `--bg-active` | `rgba(99, 102, 241, 0.12)` | 激活态背景（紫蓝 12% 透明） |

#### 暗色主题
| 变量名 | 色值 | 用途 |
|--------|------|------|
| `--vben-bg-base` | `#1e2028` | 深色基础背景 |
| `--vben-bg-elevated` | `#262a34` | 深色抬升背景 |
| `--bg-page` | `#0d0f13` | 深色页面底 |
| `--bg-sidebar` | `#16181e` | 深色侧边栏 |
| `--vben-bg-hover` | `rgba(255, 255, 255, 0.05)` | 深色 hover |
| `--vben-bg-active` | `rgba(109, 112, 246, 0.2)` | 深色激活态 |

---

### 🔲 边框色（Border Colors）

#### 亮色主题
| 变量名 | 色值 | 用途 |
|--------|------|------|
| `--vben-border` / `--border-color` | `#e5e5e5` | 默认边框 |
| `--vben-border-light` | `#f0f0f0` | 浅边框 |
| `--vben-border-dark` / `--border-input` | `#d4d4d8` | 深边框（输入框边框） |
| `--sidebar-border` | `rgba(0,0,0,0.06)` | 侧边栏极细半透明边框 |

#### 暗色主题
| 变量名 | 色值 | 用途 |
|--------|------|------|
| `--vben-border` | `#2a2d38` | 深色默认边框 |
| `--vben-border-light` | `#202329` | 深色浅边框 |
| `--vben-border-dark` | `#333745` | 深色深边框 |

---

### 🌈 扩展色板（Extended Colors）

用于状态徽标、图标背景等

| 颜色 | 色值 | 用途 | CSS 类名 |
|------|------|------|----------|
| **Purple** | `#7c3aed` | 外部系统标记 | `.tint-purple` |
| **Cyan** | `#06b6d4` | 辅助标记 | `.tint-cyan` |
| **Indigo** | `#6366f1` | 主色标记 | `.tint-indigo` |
| **Green** | `#30a46c` | 成功标记 | `.tint-green` |
| **Blue** | `#0090ff` | 信息标记 | `.tint-blue` |
| **Orange** | `#f76b15` | 警告标记 | `.tint-orange` |
| **Red** | `#e5484d` | 错误标记 | `.tint-red` |

每个颜色都有对应的半透明背景（12% 透明度）：
```css
.tint-indigo { 
  background: rgba(99, 102, 241, 0.12); 
  color: var(--vben-primary); 
}
```

---

## 字体系统

### 📏 字号（Font Size）

| 变量名 | 数值 | 用途 | 示例 |
|--------|------|------|------|
| `--vben-font-size-sm` | `12px` | 小字号 | 辅助文字、Tag、描述文字 |
| `--vben-font-size-base` | `13px` | 基础字号（全局默认） | 表格、表单、按钮、菜单 |
| `--vben-font-size-lg` | `14px` | 大字号 | 卡片标题、Modal 标题 |
| - | `15px` | 强调数字 | 统计数字 |
| - | `18px` | 父菜单图标 | 一级菜单图标 |

> **设计原则**：Linear 风格偏紧凑，基础字号采用 13px 而非常见的 14px

### ⚖️ 字重（Font Weight）

| 数值 | 用途 | 示例 |
|------|------|------|
| `400` | 常规文字 | 正文、次要文字 |
| `500` | 中等强调 | 按钮、菜单、表头、激活项 |
| `600` | 强调标题 | 卡片标题、Modal 标题、筛选标签 |
| `700` | 强烈强调（少用） | 状态徽标内部符号 |

> **Linear 特点**：一级菜单使用 `font-weight: 500` 而非 `700`，更加克制

### 📐 行高（Line Height）

| 场景 | 行高 | 说明 |
|------|------|------|
| 紧凑文本 | `1.4` | 菜单项、表格单元格 |
| 状态徽标 | `1.6` | status-badge |
| 表单标签 | `28px` | 固定高度，与小尺寸控件对齐 |
| 控件内文字 | `normal` / `30px` | 保证垂直居中 |

### ✍️ 字间距（Letter Spacing）

| 场景 | 数值 | 用途 |
|------|------|------|
| 一级菜单 | `-0.01em` | 略微压紧字间距 |
| 状态徽标 | `0.5px` | 增加可读性和精致感 |

---

## 间距系统

### 📐 间距变量

| 变量名 | 数值 | 用途 | 示例 |
|--------|------|------|------|
| `--vben-spacing-xs` | `4px` | 最小间距 | 图标与文字间隙、复选框组间距 |
| `--vben-spacing-sm` | `8px` | 小间距 | 筛选栏项目间距、表格内边距（紧凑模式） |
| `--vben-spacing` | `12px` | 默认间距 | 卡片内边距、筛选栏间距、按钮内边距、表格内边距 |
| `--vben-spacing-lg` | `16px` | 大间距 | 大按钮内边距、Modal 内边距、表单项底部间距 |
| `--vben-spacing-xl` | `24px` | 超大间距 | 页面区块间距 |

### 🎯 具体应用

#### 组件内边距
| 组件 | 内边距 | 说明 |
|------|--------|------|
| Button | `0 12px` | 默认按钮 |
| Button (small) | `0 8px` | 小按钮 |
| Button (large) | `0 16px` | 大按钮 |
| Card Body | `16px` | 默认卡片 |
| Card Body (small) | `12px` | 小卡片 |
| Card Header | `12px 16px` | 卡片头部 |
| Modal Header | `16px` | 弹窗头部 |
| Modal Body | `16px` | 弹窗内容 |
| Modal Footer | `12px 16px` | 弹窗底部 |
| Table Cell | `8px 12px` | 表格单元格 |
| Table Cell (small) | `6px 10px` | 紧凑表格 |
| Form Item | `margin-bottom: 16px` | 表单项间距 |

#### 菜单间距
| 元素 | 内边距 | 说明 |
|------|--------|------|
| 一级菜单 | `10px 12px` | 窄侧边栏优化 |
| 二级菜单 | `7px 36px 7px 12px` | 左侧缩进 36px |
| 子菜单容器 | `4px 0 8px 0` | 上下留白 |

---

## 圆角系统

### 📦 圆角变量

| 变量名 | 数值 | 用途 | 示例 |
|--------|------|------|------|
| `--vben-radius-sm` | `2px` | 小圆角 | Tag、Checkbox |
| `--vben-radius` | `4px` | 默认圆角 | Button、Input、Select、Card |
| `--vben-radius-lg` | `6px` | 大圆角 | Modal、Alert、sec-title |
| - | `12px` | 特大圆角 | status-badge（药丸形） |

> **设计原则**：Linear 风格使用较小的圆角（4px），保持简洁利落

---

## 尺寸系统

### 📏 控件高度

| 变量名 | 数值 | 用途 |
|--------|------|------|
| `--vben-control-height-sm` | `26px` | 小尺寸控件 |
| `--vben-control-height` | `32px` | 默认控件高度 |
| `--vben-control-height-lg` | `38px` | 大尺寸控件 |

**应用组件**：Button、Input、Select、InputNumber、DatePicker、Radio Button

### 🏢 布局尺寸

| 变量名 | 数值 | 用途 |
|--------|------|------|
| `@header-height` | `48px` | 顶部页眉高度 |
| `@multiple-height` | `30px` | 多标签页高度 |
| `@logo-width` | `32px` | Logo 宽度 |

### 📊 组件最小尺寸

| 组件 | 最小高度 | 说明 |
|------|----------|------|
| Menu Item (二级) | `34px` | 更紧凑的行高 |
| Select Item | `32px` | 下拉选项高度 |
| Form Label | `28px` | 表单标签行高 |

---

## 阴影系统

### 🌑 阴影规范

| 场景 | 阴影值 | 用途 |
|------|--------|------|
| **无阴影** | `none` | Card、Button（Linear 特点：去阴影） |
| **浅阴影** | `0 2px 12px 0 rgba(0, 0, 0, 0.1)` | Popover |
| **中阴影** | `0 4px 12px rgba(0, 0, 0, 0.08)` | Dropdown 下拉菜单 |
| **Input Focus** | `0 0 0 2px rgba(99, 102, 241, 0.1)` | 输入框聚焦光晕 |

> **设计原则**：Linear 风格几乎不使用阴影，依靠边框和背景色层次区分元素

---

## 组件样式规范

### 🔘 Button（按钮）

#### 尺寸规范
| 尺寸 | 高度 | 内边距 | 字号 | 字重 |
|------|------|--------|------|------|
| Small | `26px` | `0 8px` | `12px` | `500` |
| Default | `32px` | `0 12px` | `13px` | `500` |
| Large | `38px` | `0 16px` | `14px` | `500` |

#### 类型样式
| 类型 | 背景色 | 边框色 | 文字色 | Hover | Active |
|------|--------|--------|--------|-------|--------|
| **Primary** | `#6366f1` | `#6366f1` | `#ffffff` | `#4f46e5` | `#4338ca` |
| **Default** | `transparent` | `#d4d4d8` | `#1c2024` | 边框/文字转主色 | - |
| **Text** | `transparent` | `none` | `#1c2024` | 文字转主色 | - |

#### 通用属性
- **圆角**：`4px`
- **阴影**：`none`（强制去除）
- **字重**：`500`
- **过渡**：`0.15s ease`

---

### 📝 Input（输入框）

#### 尺��规范
| 尺寸 | 高度 | 字号 | 内边距 |
|------|------|------|--------|
| Small | `26px` | `12px` | `4px 11px` |
| Default | `32px` | `13px` | `4px 11px` |

#### 状态样式
| 状态 | 边框色 | 阴影 |
|------|--------|------|
| **Normal** | `#d4d4d8` | - |
| **Hover** | `#6366f1` | - |
| **Focus** | `#6366f1` | `0 0 0 2px rgba(99, 102, 241, 0.1)` |
| **Disabled** | `#e5e5e5` | - |

#### 特殊处理
- **Textarea**：`height: auto`（允许多行）
- **Input Group**：内层 input 高度设为 `100%` + `line-height: normal`（修复密码框、带清除按钮输入框的值贴底问题）

---

### 🎯 Select（下拉框）

#### 选择器样式
| 属性 | 数值 |
|------|------|
| 高度 | `32px` |
| 字号 | `13px` |
| 边框色 | `#d4d4d8` |
| 圆角 | `4px` |
| Hover 边框 | `#6366f1` |
| Focus 阴影 | `0 0 0 2px rgba(99, 102, 241, 0.1)` |

#### 下拉面板
| 属性 | 数值 |
|------|------|
| 圆角 | `6px` |
| 阴影 | `0 4px 12px rgba(0, 0, 0, 0.08)` |

#### 选项样式
| 属性 | 数值 |
|------|------|
| 高度 | `32px` |
| 内边距 | `6px 12px` |
| 行高 | `20px`（32 - 6*2） |
| 字号 | `13px` |
| Active 背景 | `rgba(0, 0, 0, 0.02)` |
| Selected 背景 | `rgba(99, 102, 241, 0.12)` |
| Selected 字重 | `500` |

---

### 📊 Table（表格）

#### 表头样式
| 属性 | 数值 |
|------|------|
| 背景色 | `#fafafa` |
| 文字色 | `#1c2024` |
| 字重 | `500` |
| 字号 | `13px` |
| 内边距 | `8px 12px` |
| 下边框 | `1px solid #e5e5e5` |

#### 表体样式
| 属性 | 数值 |
|------|------|
| 内边距 | `8px 12px` |
| 下边框 | `1px solid #f0f0f0`（浅边框） |
| Hover 背景 | `rgba(0, 0, 0, 0.02)` |
| Selected 背景 | `rgba(99, 102, 241, 0.12)` |

#### 紧凑模式
| 元素 | 内边距 |
|------|--------|
| 表头/表体 | `6px 10px` |

#### 特殊处理
- **去斑马纹**：`background: transparent`（强制覆盖）
- **行高**：紧凑设计，减少垂直空间

---

### 🎴 Card（卡片）

#### 整体样式
| 属性 | 数值 |
|------|------|
| 边框 | `1px solid #e5e5e5` |
| 圆角 | `4px` |
| 阴影 | `none` |

#### 卡片头部
| 属性 | 数值 |
|------|------|
| 背景色 | `transparent` |
| 边框底部 | `1px solid #f0f0f0` |
| 内边距 | `12px 16px` |
| 标题字号 | `14px` |
| 标题字重 | `600` |

#### 卡片内容
| 尺寸 | 内边距 |
|------|--------|
| Default | `16px` |
| Small | `12px` |

#### theme-card 类（业务常用）
- **头部背景**：`#fafafa`
- **边框**：`1px solid #e5e5e5`

---

### 🪟 Modal（弹窗）

#### 整体样式
| 属性 | 数值 |
|------|------|
| 圆角 | `6px` |

#### 头部
| 属性 | 数值 |
|------|------|
| 背景色 | `#fafafa` |
| 边框底部 | `1px solid #f0f0f0` |
| 内边距 | `16px` |
| 标题字号 | `14px` |
| 标题字重 | `600` |
| 圆角 | `6px 6px 0 0` |

#### 内容
| 属性 | 数值 |
|------|------|
| 内边距 | `16px` |
| 字号 | `13px` |

#### 底部
| 属性 | 数值 |
|------|------|
| 内边距 | `12px 16px` |
| 边框顶部 | `1px solid #f0f0f0` |

---

### 🏷️ Tag（标签）

#### 基础样式
| 属性 | 数值 |
|------|------|
| 字号 | `12px` |
| 内边距 | `2px 8px` |
| 圆角 | `2px` |
| 边框 | `none` |

#### 类型配色
| 类型 | 背景色 | 文字色 |
|------|--------|--------|
| **Default** | `#fafafa` | `#1c2024` |
| **Primary / Blue** | `rgba(99, 102, 241, 0.12)` | `#6366f1` |
| **Success / Green** | `rgba(48, 164, 108, 0.12)` | `#30a46c` |
| **Warning / Orange** | `rgba(247, 107, 21, 0.12)` | `#f76b15` |
| **Error / Red** | `rgba(229, 72, 77, 0.12)` | `#e5484d` |
| **Purple** | `rgba(124, 58, 237, 0.12)` | `#7c3aed` |

> **设计原则**：12% 透明度的浅色背景 + 对应实色文字

---

### ☑️ Checkbox / Radio（复选框/单选框）

#### 样式规范
| 属性 | 数值 |
|------|------|
| 边框圆角 | `2px` |
| 边框色 | `#d4d4d8` |
| 选中背景 | `#6366f1` |
| 选中边框 | `#6366f1` |
| 文字字号 | `13px` |
| 文字颜色 | `#1c2024` |

#### Radio Button（按钮式单选）
| 属性 | 数值 |
|------|------|
| 高度 | `32px` |
| 行高 | `30px` |
| 字号 | `13px` |
| 边框色 | `#d4d4d8` |
| 选中背景 | `rgba(99, 102, 241, 0.08)` |
| 选中边框 | `#6366f1` |
| 选中文字 | `#6366f1` |

---

### 📋 Form（表单）

#### 表单项间距
| 属性 | 数值 |
|------|------|
| margin-bottom | `16px` |

#### 标签样式
| 属性 | 数值 |
|------|------|
| 字号 | `13px` |
| 颜色 | `#60646c`（次要文字色） |
| 高度 | `28px` |
| 必填标记 | `color: #e5484d`（错误色） |

#### 垂直布局
| 属性 | 数值 |
|------|------|
| Label padding-bottom | `4px` |

#### 说明文字
| 属性 | 数值 |
|------|------|
| 字号 | `12px` |
| 颜色 | `#9ca3af`（辅助文字色） |

---

### ⚠️ Alert（提示框）

#### 整体样式
| 属性 | 数值 |
|------|------|
| 圆角 | `6px` |

#### 类型配色
| 类型 | 背景色 | 边框 | 图标色 |
|------|--------|------|--------|
| **Info** | `rgba(0, 144, 255, 0.06)` | `1px solid rgba(0, 144, 255, 0.25)` | `#0090ff` |
| **Success** | `rgba(48, 164, 108, 0.06)` | `1px solid rgba(48, 164, 108, 0.25)` | `#30a46c` |
| **Warning** | `rgba(247, 107, 21, 0.06)` | `1px solid rgba(247, 107, 21, 0.25)` | `#f76b15` |
| **Error** | `rgba(229, 72, 77, 0.06)` | `1px solid rgba(229, 72, 77, 0.25)` | `#e5484d` |

> **设计原则**：6% 透明度背景 + 25% 透明度边框 + 实色图标

---

### ✂️ Divider（分隔线）

| 属性 | 数值 |
|------|------|
| 颜色 | `#f0f0f0`（浅边框色） |

---

### 📄 Descriptions（描述列表）

#### 标签
| 属性 | 数值 |
|------|------|
| 字号 | `13px` |
| 颜色 | `#60646c`（次要文字色） |
| 字重 | `500` |

#### 内容
| 属性 | 数值 |
|------|------|
| 字号 | `13px` |
| 颜色 | `#1c2024`（主文字色） |

---

## 菜单样式规范

### 🎨 Linear 风格菜单配色

> 现代化扁平菜单主题：浅色侧边栏，一级菜单深灰块、二级菜单浅灰底，无阴影无卡片

#### 侧边栏
| 变量名 | 色值 | 说明 |
|--------|------|------|
| `@sidebar-bg` | `#f1f5f9` | Linear 侧边栏底色（Slate 100 蓝灰） |
| `@sidebar-border` | `rgba(0,0,0,0.06)` | 极细半透明边框 |

#### 一级菜单（父菜单）
| 属性 | 数值 | 说明 |
|------|------|------|
| 背景色 | `#e2e8f0` | Slate 200，比侧边栏略深 |
| 文字色 | `#18181b` | 近黑 |
| 字重 | `500` | Linear 用 500 而非 700 |
| 字号 | `13px` | 更小更紧凑 |
| 字间距 | `-0.01em` | 略微压紧 |
| 内边距 | `10px 12px` | 窄侧边栏优化 |
| 圆角 | `0` | 无圆角 |
| 边框 | `none` | Linear 不用分组边框 |
| Hover 背景 | `rgba(0,0,0,0.04)` | 半透明 |
| 图标色 | `#71717a` | 中灰 |
| 图标大小 | `18px` | - |

#### 一级菜单展开态
| 属性 | 数值 |
|------|------|
| 文字色 | `#6366f1`（激活色） |
| 图标色 | `#6366f1`（同步） |

#### 二级菜单（子菜单）
| 属性 | 数值 | 说明 |
|------|------|------|
| 背景色 | `transparent` | 无背景 |
| 文字色 | `#71717a` | 中灰 |
| 字重 | `400` | 常规 |
| 字号 | `13px` | Linear 紧凑字号 |
| 行高 | `1.4` | - |
| 最小高度 | `34px` | 更紧凑 |
| 内边距 | `7px 36px 7px 12px` | 左侧缩进 36px |
| 左指示条 | `2px solid transparent` | 默认透明 |
| 下边框 | `none` | Linear 不用分隔线 |
| Hover 背景 | `rgba(0,0,0,0.04)` | 半透明 |
| Hover 文字 | `#3f3f46` | 加深 |
| 图标色 | `#9ca3af` | 浅灰 |
| 图标大小 | `15px` | - |

#### 二级菜单激活态
| 属性 | 数值 | 说明 |
|------|------|------|
| 背景色 | `rgba(99, 102, 241, 0.12)` | 紫蓝半透明 |
| 文字色 | `#6366f1` | 淡紫 |
| 字重 | `500` | 加粗 |
| 左指示条 | `2px solid #6366f1` | Indigo 500 |
| 图标色 | `#6366f1` | 同步 |

#### 子菜单容器
| 属性 | 数值 |
|------|------|
| 背景色 | `transparent` |
| 内边距 | `4px 0 8px 0` |

---

### 📐 内容区背景

| 元素 | 背景色 | 说明 |
|------|--------|------|
| `.vben-layout-content` | `#fafafa` | 浅灰内容区 |
| `.vben-page-wrapper` | `#fafafa` | 页面包装器 |
| `.vben-page-wrapper-content` | `#fafafa` | 页面内容 |

> **层次分明**：侧边栏 `#f1f5f9` + 内容区 `#fafafa`，细微差异营造立体感

---

## 业务组件样式

### 🏷️ status-badge（状态徽标）

> 用于 Pass/Fail/Error/Skipped 等状态显示，全系统统一

#### 基础样式
| 属性 | 数值 |
|------|------|
| display | `inline-flex` |
| align-items | `center` |
| justify-content | `center` |
| padding | `2px 12px` |
| border-radius | `12px`（药丸形） |
| font-size | `12px` |
| font-weight | `600` |
| letter-spacing | `0.5px` |
| min-width | `52px` |
| line-height | `1.6` |
| white-space | `nowrap` |

#### 类型配色
| 类型 | 背景色 | 文字色 | 边框 | 图标 |
|------|--------|--------|------|------|
| **Passed** | `rgba(48, 164, 108, 0.12)` | `#30a46c` | `1px solid rgba(48, 164, 108, 0.35)` | ✓ |
| **Failed** | `rgba(248, 113, 113, 0.12)` | `#e5484d` | `1px solid rgba(248, 113, 113, 0.25)` | ✗ |
| **Error** | `rgba(229, 72, 77, 0.14)` | `#e5484d` | `1px solid rgba(229, 72, 77, 0.3)` | ⚠ |
| **Skipped** | `rgba(247, 107, 21, 0.12)` | `#f76b15` | `1px solid rgba(247, 107, 21, 0.25)` | – |

#### 图标样式
- **font-weight**: `700`
- **margin-right**: `4px`
- **内容**: 通过 `::before` 伪元素插入

#### 使用示例
```html
<span class="status-badge passed">PASS</span>
<span class="status-badge failed">FAIL</span>
<span class="status-badge error">ERROR</span>
<span class="status-badge skipped">SKIP</span>
```

---

### 🎨 sec-title（区块标题）

> 图标 + 浅色系彩色块，全系统统一的区块标题样式

#### 基础样式
| 属性 | 数值 |
|------|------|
| display | `inline-flex` |
| align-items | `center` |
| gap | `6px` |
| font-weight | `600` |
| font-size | `13px` |
| line-height | `1` |
| padding | `5px 10px` |
| border-radius | `6px` |

#### 颜色变体（Tint Classes）
| 类名 | 背景色 | 文字色 | 色系 |
|------|--------|--------|------|
| `.tint-indigo` | `rgba(99, 102, 241, 0.12)` | `#6366f1` | Indigo |
| `.tint-green` | `rgba(48, 164, 108, 0.12)` | `#30a46c` | Green |
| `.tint-blue` | `rgba(0, 144, 255, 0.12)` | `#0090ff` | Blue |
| `.tint-orange` | `rgba(247, 107, 21, 0.12)` | `#f76b15` | Orange |
| `.tint-red` | `rgba(229, 72, 77, 0.12)` | `#e5484d` | Red |
| `.tint-purple` | `rgba(124, 58, 237, 0.12)` | `#7c3aed` | Purple |
| `.tint-cyan` | `rgba(6, 182, 212, 0.12)` | `#06b6d4` | Cyan |

#### 使用示例
```html
<div class="sec-title tint-indigo">
  <icon-park-outline:file-text />
  <span>测试报告</span>
</div>
```

---

### 🎛️ filter-bar（筛选栏）

#### filter-card（筛选卡片）
| 属性 | 数值 |
|------|------|
| border | `1px solid #e5e5e5` |

#### filter-bar（筛选栏容器）
| 属性 | 数值 |
|------|------|
| gap | `8px` |

#### filter-group（筛选组）
| 属性 | 数值 |
|------|------|
| gap | `8px` |

#### filter-label（筛选标签）
| 属性 | 数值 |
|------|------|
| color | `#60646c`（次要文字色） |
| font-size | `13px` |
| font-weight | `600` |
| line-height | `32px`（和控件对齐） |

#### filter-section-title（区块标题）
| 属性 | 数值 |
|------|------|
| font-size | `13px` |
| font-weight | `600` |
| color | `#60646c` |

#### filter-actions（操作区）
| 属性 | 数值 |
|------|------|
| gap | `12px` |
| padding-top | `8px` |
| border-top | `1px dashed #e5e5e5` |

---

### 🔧 toolbar（工具栏）

#### toolbar 容器
| 属性 | 数值 |
|------|------|
| display | `flex` |
| align-items | `center` |
| gap | `12px` |
| flex-wrap | `wrap` |

#### toolbar .label（标签）
| 属性 | 数值 |
|------|------|
| font-size | `13px` |
| font-weight | `600` |
| color | `#60646c` |

#### toolbar .hint（提示）
| 属性 | 数值 |
|------|------|
| font-size | `12px` |
| color | `#9ca3af` |

---

### 📊 统计数字

#### hit-count / stat-number
| 属性 | 数值 |
|------|------|
| color | `#6366f1`（主色） |
| font-size | `13px` |
| font-weight | `600` |

#### hit-count strong / stat-number strong
| 属性 | 数值 |
|------|------|
| color | `#6366f1` |
| font-size | `15px` |

---

### 🎨 文字颜色工具类

| 类名 | 颜色 | 用途 |
|------|------|------|
| `.text-success` | `#30a46c` | 成功状态 |
| `.text-warning` | `#f76b15` | 警告状态 |
| `.text-error` | `#e5484d` | 错误状态 |
| `.text-info` | `#0090ff` | 信息状态 |
| `.text-muted` | `#9ca3af` | 辅助文字 |

---

### 📝 mark-desc（标记描述）

| 属性 | 数值 |
|------|------|
| color | `#9ca3af` |
| font-size | `12px` |

#### mark-checkbox-group（标记复选框组）
| 属性 | 数值 |
|------|------|
| gap | `4px 12px`（行间距 4px，列间距 12px） |

---

### 🎚️ radio-and / radio-or（特殊单选按钮）

#### radio-and 选中态
| 属性 | 数值 |
|------|------|
| border-color | `#6366f1` |
| color | `#6366f1` |

#### radio-or 选中态
| 属性 | 数值 |
|------|------|
| border-color | `#f76b15` |
| color | `#f76b15` |

---

## 响应式断点

### 📱 断点定义

| 断点名称 | 最小宽度 | 最大宽度 | 设备类型 |
|----------|----------|----------|----------|
| **xs** | `320px` | `639px` | 超小屏 / 手机 |
| **sm** | `640px` | `767px` | 小屏 / 平板 |
| **md** | `768px` | `959px` | 中屏 / 桌面 |
| **lg** | `960px` | `1279px` | 大屏 / 宽桌面 |
| **xl** | `1280px` | `1535px` | 超大屏 / 全高清 |
| **2xl** | `1536px` | - | 超超大屏 / 大桌面 |

### 📐 小屏幕优化（≤ 768px）

#### 变量调整
| 变量名 | 桌面值 | 移动值 |
|--------|--------|--------|
| `--vben-font-size-base` | `13px` | `12px` |
| `--vben-spacing` | `12px` | `8px` |
| `--vben-control-height` | `32px` | `28px` |

#### 组件调整
| 组件 | 属性 | 移动值 |
|------|------|--------|
| Card Body | padding | `12px` |
| Table Cell | padding | `6px 8px` |

---

## 过渡动画

### ⏱️ 过渡时长

| 场景 | 时长 | 曲线 | 说明 |
|------|------|------|------|
| 颜色变化 | `0.15s` | `ease` | 背景色、文字色、边框色 |
| 快速交互 | `0.12s` | `ease` | 菜单项悬停 |
| 自动填充 | `5000s` | `ease-in-out` | 防止浏览器自动填充背景闪烁 |

### 🎬 过渡动画类型

项目包含完整的过渡动画系统：

#### 可用过渡类型
- **fade**：淡入淡出
- **scale**：缩放
- **slide**：滑动
- **scroll**：滚动
- **zoom**：放大缩小

> 详细定义见 `src/design/transition/` 目录

---

## 滚动条样式

### 📜 滚动条规范

#### Linear 风格（极细滚动条）
| 属性 | 数值 | 说明 |
|------|------|------|
| 宽度 | `6px` | 垂直滚动条 |
| 高度 | `6px` | 水平滚动条 |
| 轨道背景 | `transparent` | 透明 |
| 滑块背景 | `rgba(0, 0, 0, 0.1)` | 10% 黑色透明 |
| 滑块圆角 | `3px` | 半圆角 |
| 滑块 hover | `rgba(0, 0, 0, 0.2)` | 20% 黑色透明 |

#### 传统风格（备选）
| 属性 | 数值 |
|------|------|
| 宽度 | `7px` |
| 高度 | `8px` |
| 轨道背景 | `rgba(0, 0, 0, 0.05)` |
| 滑块背景 | `rgba(144, 147, 153, 0.3)` |
| 滑块圆角 | `2px` |
| 滑块阴影 | `inset 0 0 6px rgba(0, 0, 0, 0.2)` |
| 滑块 hover | `#b6b7b9` |

---

## Z-Index 层级系统

| 变量名 | 数值 | 用途 |
|--------|------|------|
| `@page-footer-z-index` | `99` | 页脚 |
| `@side-drag-z-index` | `200` | 侧边栏拖拽 |
| `@layout-header-fixed-z-index` | `500` | 固定页眉 |
| `@multiple-tab-fixed-z-index` | `505` | 固定多标签页 |
| `@layout-sider-fixed-z-index` | `510` | 固定侧边栏 |
| `@layout-mix-sider-fixed-z-index` | `550` | 混合布局侧边栏 |
| `@preview-comp-z-index` | `1000` | 预览组件 |
| `@lock-page-z-index` | `3000` | 锁屏页 |
| `@page-loading-z-index` | `10000` | 页面加载 |

---

## 设计原则总结

### 🎯 核心特征

1. **极简主义**：去阴影、小圆角、扁平化
2. **紧凑设计**：13px 基础字号、32px 控件高度、紧密间距
3. **清晰层次**：依靠背景色和边框区分层次，而非阴影
4. **一致配色**：12% 透明度的浅色背景 + 对应实色文字
5. **克制字重**：一级菜单用 500 而非 700，避免过重
6. **细腻边框**：极细半透明边框（`rgba(0,0,0,0.06)`）
7. **紫蓝主色**：Indigo 500（`#6366f1`）贯穿全局
8. **Radix 语义色**：专业的语义色系统

### 🚀 迁移建议

#### 优先级 1（核心）
- 色彩变量（主色、语义色、文字色、背景色、边框色）
- 字体系统（字号、字重）
- 间距系统
- 圆角系统

#### 优先级 2（组件）
- Button、Input、Select 样式
- Table、Card 样式
- Menu 样式（菜单是 Linear 风格的核心）

#### 优先级 3（业务）
- status-badge（状态徽标）
- sec-title（区块标题）
- filter-bar（筛选栏）
- 文字颜色工具类

#### 优先级 4（扩展）
- 过渡动画
- 滚动条样式
- 响应式调整

---

## 文件对应关系

本清单中的规则分布在以下实际文件里（目录结构见 README §4）：

| 规则 | 文件 |
|---|---|
| 色彩 / 尺寸变量、组件覆盖、status-badge、sec-title、tint-*、滚动条、响应式 | `theme/linear-components.css` |
| 业务语义变量（`--bg-*` / `--text-*` / `--accent`）、`.theme-card` | `theme/theme-vars.less` |
| 侧边栏菜单 | `theme/menu-theme.less` |
| antd Design Token | `theme/antd-theme-token.ts` |
| 页内标签 FlowTabs | `components/FlowTabs.vue` |

---

## 兼容性说明

### 浏览器支持
- Chrome / Edge（Chromium）：完全支持
- Firefox：完全支持
- Safari：完全支持（需注意 CSS 变量和伪元素）

### CSS 特性依赖
- CSS 变量（Custom Properties）
- Flexbox
- CSS Grid（可选）
- `:where()` 伪类（用于降低特异性）
- `::before` / `::after` 伪元素

### Ant Design Vue 版本
- 推荐版本：4.x（`antd-theme-token.ts` 使用 4.x 的 ConfigProvider theme 格式）
- 需要覆盖的组件：所有基础组件

---

## 变更日志

### v1.0.0（当前版本）
- 完整提取 Linear 风格设计系统
- 包含亮色/暗色两套主题
- 覆盖所有基础组件和业务组件
- 提供完整的变量系统和工具类

---

**文档生成时间**：2026-11-26  
**基于项目**：rpa-test-automation/web-vben  
**目标项目**：at-web-theme-kit  

