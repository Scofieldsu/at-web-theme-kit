# at-web-theme-kit 项目总结

## 完成日期
2026-11-26

## 项目概述

at-web-theme-kit 是从 rpa-test-automation 项目提取的 **Linear 风格设计系统**，完全解耦业务逻辑，可直接复用到任何 Vue 3 + Ant Design Vue 4 项目。

---

## 核心特性

### 1. 设计基调：浅色紧凑的 Linear 风

- **单一强调色**：Indigo `#6366f1` 贯穿全系统
- **语义色只做淡底**：12% 透明度 + 同色文字 + 细边框
- **扁平化**：无阴影、小圆角（4px）、小字号（13px）
- **亮暗双主题**：CSS 变量驱动，一键切换

### 2. 完整的设计系统

#### 色彩系统
- 主题色：Indigo 阶梯度（3 档）
- 语义色：Radix UI 色板（Success/Warning/Error/Info）
- 文字色：4 层级（主/次要/辅助/禁用）
- 背景色：6 种场景
- 边框色：3 层级
- 扩展色板：7 种额外颜色

#### 尺寸系统
- 字号：13px 基准（比默认 14px 更紧凑）
- 控件高度：32px 标准 / 38px 大 / 26px 小
- 圆角：4px 基准 / 6px 大 / 2px 小
- 间距：12px 基准（5 个层级）

#### 组件覆盖
13 个核心组件完整样式规范：
Button / Input / Select / Table / Card / Modal / Form / Tag / Checkbox / Radio / Alert / Divider / Descriptions

---

## 文件结构

```
at-web-theme-kit/
├── README.md                    # 设计规范概览（25KB）
├── DESIGN_SPEC.md               # 完整设计系统清单（31KB，1089 行）
├── INTEGRATION_GUIDE.md         # 接入指南（5KB）
├── theme/                       # 主题资产文件（4 个）
│   ├── antd-theme-token.ts      # Ant Design ConfigProvider token
│   ├── linear-components.css    # CSS 变量 + 组件全局覆盖（21KB）
│   ├── theme-vars.less          # 业务语义变量
│   └── menu-theme.less          # 侧边栏菜单专项
└── components/                  # 业务组件
    ├── FlowTabs.vue             # 页内标签组件（3KB）
    └── FlowTabs.md              # FlowTabs 设计规范
```

---

## 核心创新：FlowTabs 页内标签

### 设计理念
传统多级菜单适合导航型应用，但对于线性工作流（测试流程、配置向导等），传统菜单会打断流程连贯性。

**Linear 风格菜单结构**采用：
1. hideChildrenInMenu：隐藏二级菜单项
2. FlowTabs 页内标签：彩色芯片标签切换各子步骤
3. meta.color 语义配色：一级菜单按流程语义配色

### FlowTabs 特性
- **4 色循环**：绿/蓝/紫/橙
- **3 态视觉**：未激活白底彩边 → hover 8%淡底 → 激活实色背景
- **URL 同步**：通过 `?tab=xxx` 支持直接链接
- **圆角 8px**：比全局 4px 大，强调标签感
- **字重 600**：突出流程步骤

---

## 在 at-web 项目中的应用

### 更新内容

1. **新增 FlowTabs 组件**
   - `src/views/platform/components/FlowTabs.vue`
   
2. **新增流程主页**（4 个）
   - `PrepareHome.vue` - 环境准备
   - `MessageHome.vue` - 消息模拟
   - `TestFlow.vue` - 测试执行
   - `FaultHome.vue` - 故障模拟

3. **路由结构重组**
   - 使用 `hideChildrenInMenu` 隐藏子菜单
   - 子路由改为 redirect 到主页 + query tab
   - 保留原路径兼容性

4. **菜单配色统一**
   - 总览：`#6366f1` (Indigo)
   - 环境准备：`#30a46c` (Green)
   - 故障模拟：`#e5484d` (Red)
   - 消息模拟：`#0090ff` (Blue)
   - 测试执行：`#f76b15` (Orange)
   - 版本记录：`#7c3aed` (Purple)
   - 系统配置：`#64748b` (Slate)
   - 外链直达：`#06b6d4` (Cyan)

### 修改的文件（9 个）
- `router/routes/modules/platform.ts` - 重组测试流程路由
- `router/routes/modules/fault.ts` - 故障模拟改用 FlowTabs
- `views/platform/Dashboard.vue` - 更新链接指向新路由
- `views/platform/MessageSniffer.vue` - 更新跳转链接
- `views/platform/distributed/monitor.vue` - 更新机器页链接

---

## 接入步骤（3 步）

### 第 1 步：复制主题文件
```bash
cp -r at-web-theme-kit/theme/* your-project/src/design/
```

### 第 2 步：引入 CSS 和 Less
```typescript
import '@/design/linear-components.css';
import '@/design/menu-theme.less';
import '@/design/theme-vars.less';
```

### 第 3 步：配置 ConfigProvider
```vue
<ConfigProvider :theme="linearTheme">
  <App />
</ConfigProvider>
```

---

## 设计规范文档

### README.md（主文档）
- 一句话设计规则
- 设计基调（4 个关键词）
- 完整配色体系（6 大类）
- 风格签名（13 个维度）
- 资产清单
- 接入步骤
- **菜单结构设计模式**（新增）
- 日常调整入口

### DESIGN_SPEC.md（详细规范）
1089 行完整清单，包含：
- 色彩系统（所有色值 + 用途）
- 字体系统（字号/字重/行高/字间距）
- 间距系统（5 层级 + 应用表格）
- 圆角系统（4 层级）
- 尺寸系统（控件/布局/最小尺寸）
- 阴影系统
- 13 个组件详细规范
- 菜单样式完整规范
- 9 个业务组件样式
- 响应式断点
- 过渡动画 + 滚动条 + Z-Index

### INTEGRATION_GUIDE.md（接入指南）
- 快速开始（3 步）
- FlowTabs 组件使用
- 业务组件示例
- 菜单配色约定
- 深色主题切换
- 常见问题 FAQ

---

## 设计原则

1. **极简主义**：去阴影、小圆角、扁平化
2. **紧凑设计**：13px 字号、32px 控件、8-16px 间距
3. **清晰层次**：依靠背景色和边框，而非阴影
4. **一致配色**：12% 透明度 + 对应实色文字
5. **克制字重**：一级菜单用 500 而非 700
6. **细腻边框**：极细半透明边框
7. **紫蓝主色**：Indigo 500 贯穿全局
8. **Radix 语义色**：专业的语义色系统

---

## 兼容性

### 浏览器支持
- Chrome / Edge（Chromium）：完全支持
- Firefox：完全支持
- Safari：完全支持

### 技术依赖
- Vue 3
- Ant Design Vue 4
- CSS 变量（Custom Properties）
- Flexbox

---

## 使用场景

### 适用项目
- 后台管理系统
- 测试平台
- 配置中心
- 运维控制台
- 数据分析平台
- 任何需要紧凑、高信息密度的 B 端系统

### 核心优势
1. **开箱即用**：复制 theme/ 目录即可
2. **完全解耦**：无业务代码，纯设计系统
3. **文档完整**：1000+ 行详细规范
4. **双主题支持**：亮色/暗色一键切换
5. **现代设计**：Linear 风格，紧凑美观
6. **易于定制**：CSS 变量驱动，改色值即可

---

## 下一步计划

1. ✅ 提取完整设计系统
2. ✅ 创建详细文档
3. ✅ 在 at-web 项目中验证
4. ⏳ 收集使用反馈
5. ⏳ 发布 npm 包（可选）
6. ⏳ 增加更多业务组件示例

---

**维护者**：Design System Team  
**版本**：v1.0.0  
**最后更新**：2026-11-26
