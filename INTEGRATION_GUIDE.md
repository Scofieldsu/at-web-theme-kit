# Linear 风格主题接入指南

> 本指南说明如何将 at-web-theme-kit 接入到新的 Vue 3 + Ant Design Vue 4 项目中

---

## 快速开始（3 步接入）

### 第 1 步：复制主题文件

```bash
# 将 theme/ 目录整体复制到你的项目
cp -r at-web-theme-kit/theme/* your-project/src/design/
```

### 第 2 步：引入 CSS 和 Less

在项目入口文件（如 `main.ts`）引入：

```typescript
// 引入主题 CSS（包含所有变量和组件覆盖）
import '@/design/linear-components.css';
import '@/design/menu-theme.less';
import '@/design/theme-vars.less';
```

### 第 3 步：配置 Ant Design Vue ConfigProvider

```vue
<template>
  <ConfigProvider :theme="themeConfig">
    <App />
  </ConfigProvider>
</template>

<script setup lang="ts">
import { ConfigProvider } from 'ant-design-vue';
import { linearTheme } from '@/design/antd-theme-token';
import { computed } from 'vue';

// 假设你有一个 dark mode 状态
const isDark = computed(() => document.documentElement.dataset.theme === 'dark');

const themeConfig = computed(() => {
  if (isDark.value) {
    // 深色主题时，合并深色 token
    return {
      ...linearTheme,
      token: {
        ...linearTheme.token,
        colorBgContainer: '#1e2028',
        // 其他深色覆盖...
      }
    };
  }
  return linearTheme;
});
</script>
```

---

## 组件使用指南

### FlowTabs 页内标签

用于将多个相关页面整合到一个容器中，适合线性工作流。

#### 1. 复制组件

```bash
cp at-web-theme-kit/components/FlowTabs.vue your-project/src/components/
```

#### 2. 使用示例

```vue
<template>
  <FlowTabs :tabs="tabs" />
</template>

<script setup lang="ts">
import { DownloadOutlined, GlobalOutlined } from '@ant-design/icons-vue';
import FlowTabs from '@/components/FlowTabs.vue';
import type { FlowTab } from '@/components/FlowTabs.vue';
import Step1 from './Step1.vue';
import Step2 from './Step2.vue';

const tabs: FlowTab[] = [
  { key: 'step1', title: '第一步', icon: DownloadOutlined, view: Step1 },
  { key: 'step2', title: '第二步', icon: GlobalOutlined, view: Step2 },
];
</script>
```

#### 3. 路由配置

```typescript
{
  path: '/workflow',
  name: 'Workflow',
  component: LAYOUT,
  redirect: '/workflow/home',
  meta: {
    icon: 'ant-design:experiment-outlined',
    title: '工作流',
    color: '#6366f1',  // 菜单配色
    hideChildrenInMenu: true,  // 隐藏子菜单
  },
  children: [
    {
      path: 'home',
      name: 'WorkflowHome',
      component: () => import('@/views/WorkflowHome.vue'),
      meta: { title: '工作流' },
    },
    // 兼容路由（隐藏在菜单中）
    {
      path: 'step1',
      redirect: { path: '/workflow/home', query: { tab: 'step1' } },
      meta: { hideMenu: true },
    },
  ],
}
```

---

## 业务组件

### status-badge 状态徽标

```vue
<span class="status-badge passed">✓ 通过</span>
<span class="status-badge failed">✗ 失败</span>
<span class="status-badge error">⚠ 错误</span>
<span class="status-badge skipped">– 跳过</span>
```

样式已包含在 `linear-components.css` 中。

### sec-title 区块标题

```vue
<div class="sec-title tint-indigo">
  <IconComponent /> 区块标题
</div>
```

可用的 tint 类：`tint-indigo` / `tint-green` / `tint-blue` / `tint-orange` / `tint-red` / `tint-purple` / `tint-cyan`

### theme-card 变量化卡片

```vue
<a-card class="theme-card">
  <template #title>卡片标题</template>
  卡片内容
</a-card>
```

---

## 菜单配色

在路由 meta 中添加 `color` 字段：

```typescript
meta: {
  icon: 'ant-design:tool-outlined',
  title: '环境准备',
  color: '#30a46c',  // 绿色
}
```

推荐配色：

- 总览：`#6366f1` (Indigo)
- 准备/成功：`#30a46c` (Green)
- 故障/错误：`#e5484d` (Red)
- 消息/信息：`#0090ff` (Blue)
- 执行/警告：`#f76b15` (Orange)
- 特殊/归档：`#7c3aed` (Purple)
- 配置/中性：`#64748b` (Slate)
- 外部系统：`#06b6d4` (Cyan)

---

## 深色主题切换

```typescript
// 切换主题
function toggleTheme() {
  const html = document.documentElement;
  const current = html.dataset.theme;
  html.dataset.theme = current === 'dark' ? 'light' : 'dark';
}
```

CSS 变量会自动响应 `html[data-theme='dark']`。

---

## 常见问题

### Q1: 如何自定义主色？

修改 `theme/antd-theme-token.ts`：

```typescript
token: {
  colorPrimary: '#yourcolor',  // 改为你的主色
}
```

同时修改 `theme/linear-components.css` 中的 `--vben-primary` 变量。

### Q2: 表格斑马纹如何启用？

删除 `linear-components.css` 中的以下规则：

```css
/* 去掉斑马纹 */
.ant-table-tbody > tr.ant-table-row:nth-child(2n) > td {
  background: transparent !important;
}
```

### Q3: FlowTabs 如何自定义颜色？

修改 `FlowTabs.vue` 中的 `.chip-a/b/c/d` 样式。

---

## 完整示例项目

参考 `at-web` 项目的以下文件：

- 路由配置：`src/router/routes/modules/platform.ts`
- 主题配置：`src/design/index.less`
- FlowTabs 使用：`src/views/platform/PrepareHome.vue`
- 菜单配置：`src/components/Menu/src/components/MenuItemContent.vue`

---

## 技术支持

- 完整设计规范：[DESIGN_SPEC.md](./DESIGN_SPEC.md)
- 设计原则：[README.md](./README.md)
- FlowTabs 规范：[components/FlowTabs.md](./components/FlowTabs.md)
