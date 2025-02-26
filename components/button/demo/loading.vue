<docs>
---
order: 2
title:
  zh-CN: 加载中状态
  en-US: Loading
---

## zh-CN

添加 `loading` 属性即可让按钮处于加载状态，最后两个按钮演示点击后进入加载状态。

## en-US

A loading indicator can be added to a button by setting the `loading` property on the `Button`.
</docs>

<template>
  <a-space style="width: 100%">
    <a-button type="primary" loading>Loading</a-button>
    <a-button type="primary" size="small" loading>Loading</a-button>
  </a-space>
  <a-space style="width: 100%">
    <a-button type="primary" :loading="loading" @mouseenter="loading = true">
      mouseenter me!
    </a-button>
    <a-button type="primary" :loading="iconLoading" @click="enterIconLoading">
      <template #icon><PoweroffOutlined /></template>
      延迟1s
    </a-button>
  </a-space>
  <a-space style="width: 100%">
    <a-button type="primary" loading />
    <a-button type="primary" shape="circle" loading />
    <a-button type="danger" shape="round" loading />
  </a-space>
  <br />
  <a-button>Secondary</a-button>
  <a-button loading>Secondary(loading)</a-button>
  <br />
  <a-button type="text">Text</a-button>
  <a-button type="text" loading>Text(loading)</a-button>
  <br />
  <a-button type="danger">Danger Default</a-button>
  <a-button type="danger" loading>Danger Default(loading)</a-button>
  <br />
  <a-button type="text-danger">Danger Text</a-button>
  <a-button type="text-danger" loading>Danger Text(loading)</a-button>
</template>
<script lang="ts">
import { defineComponent, ref } from 'vue';
import { PoweroffOutlined } from '@ant-design/icons-vue';

interface DelayLoading {
  delay: number;
}
export default defineComponent({
  components: { PoweroffOutlined },
  setup() {
    const iconLoading = ref<boolean | DelayLoading>(false);
    const enterIconLoading = () => {
      iconLoading.value = { delay: 1000 };

      setTimeout(() => {
        iconLoading.value = false;
      }, 6000);
    };
    return {
      loading: ref(false),
      iconLoading,
      enterIconLoading,
    };
  },
});
</script>
