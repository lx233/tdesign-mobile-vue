<template>
  <div class="tdesign-mobile-demo">
    <h1 class="title">Collapse 折叠面板</h1>
    <p class="summary">在折叠面板中放入内容，点击面板的标题可以展开或收缩其内容。</p>
    <tdesign-demo-block header="01 类型" summary="基础折叠面板">
      <baseVue />
    </tdesign-demo-block>
    <tdesign-demo-block summary="带操作说明">
      <actionVue />
    </tdesign-demo-block>
    <tdesign-demo-block summary="手风琴式">
      <accordionVue />
    </tdesign-demo-block>
  </div>
</template>

<script lang="ts">
import { reactive, toRefs, defineComponent } from 'vue';
import baseVue from './base.vue';
import accordionVue from './accordion.vue';
import actionVue from './action.vue';

export default defineComponent({
  components: {
    baseVue,
    accordionVue,
    actionVue,
  },
  setup() {
    const panels = [
      {
        header: '基础面板',
        name: '0',
        content:
          '一段很长很长的内容文字一段很长很长的内容文字一段很长很长的内容文字一段很长很长的内容文字一段很长很长的内容文字一段很长很长的内容文字一段很长很长的内容文字一段很长很长的内容文字一段很长很长的内容文字',
      },
      {
        header: '内容列表',
        name: '1',
        content: ['一段很长很长的内容文字', '一段很长很长的内容文字', '一段很长很长的内容文字'],
      },
      {
        header: '内容带标签',
        extra: '预设文本',
        content: [
          { label: '标题1', content: '预设文本' },
          { label: '类目标题2', content: '预设文本' },
          {
            label: '很长很长很长的内容标题',
            content: '一段很长很长的内容文字一段很长很长的内容文字一段很长很长的内容文字',
          },
        ],
      },
      {
        header: '内容带标签 - 宽度固定',
        extra: '预设文本',
        labelWidth: 80,
        content: [
          { label: '标题1', content: '预设文本' },
          {
            label: '很长很长很长的内容标题',
            content: '一段很长很长的内容文字一段很长很长的内容文字一段很长很长的内容文字',
          },
        ],
      },
    ];
    const panelOthers = [
      {
        header: '仅点击右侧按钮展开',
        name: 'demoOnlyIconClicable',
        headerClickable: false,
        content: '点击面板右侧按钮展开/折叠',
      },
      {
        header: '禁用项',
        name: 'demoDisabled',
        disabled: true,
        content: '预设文本',
      },
      {
        header: '内容默认slot',
        name: 'slotContent',
      },
    ];
    const state = reactive({
      valueBase: ['0', 3],
      panels,
      panelOthers,
    });
    return {
      ...toRefs(state),
    };
  },
});
</script>
