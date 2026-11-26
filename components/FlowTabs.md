# FlowTabs 页内标签组件设计规范

## 概述

FlowTabs 用于将多个相关页面整合到一个容器中，通过彩色芯片标签切换。  
适用场景：环境准备、消息模拟、故障模拟、测试执行等多步骤流程页面。

## 类型定义

```typescript
export interface FlowTab {
  /** 标签唯一标识，用于 URL query 参数 */
  key: string;
  /** 标签显示文本 */
  title: string;
  /** 标签图标组件（来自 @ant-design/icons-vue） */
  icon: Component;
  /** 标签对应的视图组件 */
  view: Component;
}
```

## 使用示例

```vue
<template>
  <FlowTabs :tabs="tabs" />
</template>

<script setup lang="ts">
import FlowTabs from './components/FlowTabs.vue';
import type { FlowTab } from './components/FlowTabs.vue';
import { IconComponent1, IconComponent2 } from '@ant-design/icons-vue';
import Step1View from './Step1.vue';
import Step2View from './Step2.vue';

const tabs: FlowTab[] = [
  { key: 'step1', title: '第一步', icon: IconComponent1, view: Step1View },
  { key: 'step2', title: '第二步', icon: IconComponent2, view: Step2View },
];
</script>
```
## 设计规范

### 1. 色彩：4 种语义色循环（chip-a/b/c/d）

- **chip-a**: `#30a46c` (绿色 - 成功/准备)
- **chip-b**: `#0090ff` (蓝色 - 信息/数据流)
- **chip-c**: `#6366f1` (紫色 - 主色/重点)
- **chip-d**: `#f76b15` (橙色 - 执行/警告)

### 2. 状态

- **未激活**：白底 + 彩色边框 + 彩色文字
- **hover**：8% 半透明彩色背景
- **激活**：实色背景 + 白色文字

### 3. 尺寸

- padding: `7px 14px`
- 圆角: `8px`（比全局 4px 大，更突出）
- 字重: `600`
- 间距: `8px`

### 4. 布局

- 外层容器 padding: `16px`
- 内层页面组件 padding: `0`（由 `:deep` 覆盖）
- tab 切换保留 URL query，支持直接链接

## 组件源码

见 `FlowTabs.vue` 完整实现。

