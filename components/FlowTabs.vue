<template>
  <div class="flow-page">
    <a-tabs class="flow-tabs" :activeKey="tab" destroy-inactive-tab-pane @change="onTabChange">
      <a-tab-pane v-for="(item, index) in tabs" :key="item.key">
        <template #tab>
          <span class="menu-chip" :class="chipClass(index)">
            <component :is="item.icon" />{{ item.title }}
          </span>
        </template>
        <component :is="item.view" />
      </a-tab-pane>
    </a-tabs>
  </div>
</template>

<script lang="ts" setup>
  import type { Component } from 'vue';
  import { computed } from 'vue';
  import { useRoute, useRouter } from 'vue-router';

  export interface FlowTab {
    key: string;
    title: string;
    icon: Component;
    view: Component;
  }

  const props = defineProps<{ tabs: FlowTab[] }>();

  const route = useRoute();
  const router = useRouter();
  const chips = ['chip-a', 'chip-b', 'chip-c', 'chip-d'];

  const tab = computed(() => {
    const q = String(route.query.tab || '');
    return props.tabs.some((item) => item.key === q) ? q : props.tabs[0]?.key || '';
  });

  function chipClass(index: number) {
    return chips[index % chips.length];
  }

  function onTabChange(key: string | number) {
    const next = String(key);
    if (next === tab.value) return;
    router.replace({ path: route.path, query: { ...route.query, tab: next } });
  }
</script>

<style lang="less" scoped>
  .flow-page {
    padding: 16px;

    :deep(.page),
    :deep(.intercept-container),
    :deep(.weaknet-container),
    :deep(.patch-container),
    :deep(.popup-sim-container) {
      padding: 0;
    }
  }

  .flow-tabs {
    :deep(.ant-tabs-nav) {
      margin-bottom: 12px;

      &::before {
        border-bottom: 1px solid rgba(15, 23, 42, 0.12);
      }
    }

    :deep(.ant-tabs-ink-bar) {
      display: none;
    }

    :deep(.ant-tabs-nav-list) {
      gap: 8px;
    }

    :deep(.ant-tabs-tab),
    :deep(.ant-tabs-tab + .ant-tabs-tab) {
      margin: 0;
      padding: 0;
      background: transparent;
    }
  }

  .menu-chip {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    padding: 7px 14px;
    border: 1px solid transparent;
    border-radius: 8px;
    background: #fff;
    font-weight: 600;
    line-height: 1.2;
  }

  .chip-a {
    border-color: #30a46c;
    color: #30a46c;
  }

  .chip-b {
    border-color: #0090ff;
    color: #0090ff;
  }

  .chip-c {
    border-color: #6366f1;
    color: #6366f1;
  }

  .chip-d {
    border-color: #f76b15;
    color: #f76b15;
  }

  :deep(.ant-tabs-tab:not(.ant-tabs-tab-active):hover) {
    .chip-a { background: rgba(48, 164, 108, 0.08); }
    .chip-b { background: rgba(0, 144, 255, 0.08); }
    .chip-c { background: rgba(99, 102, 241, 0.08); }
    .chip-d { background: rgba(247, 107, 21, 0.08); }
  }

  :deep(.ant-tabs-tab-active) {
    .chip-a {
      border-color: #30a46c;
      background: #30a46c;
      color: #fff;
    }

    .chip-b {
      border-color: #0090ff;
      background: #0090ff;
      color: #fff;
    }

    .chip-c {
      border-color: #6366f1;
      background: #6366f1;
      color: #fff;
    }

    .chip-d {
      border-color: #f76b15;
      background: #f76b15;
      color: #fff;
    }
  }

  :deep(.page) {
    padding: 0;
  }
</style>
