<template>
  <div>
    <t-cell-group title="基础输入框">
      <t-input
        v-model="text"
        label="标准五个字"
        placeholder="预设文本(非必填)"
        @focus="onFocus"
        @blur="onBlur"
        @change="onChange"
      >
        <template #rightIcon>
          <t-icon-help-circle-filled />
        </template>
      </t-input>
      <t-input label="一个很长的标题需换行" placeholder="预设文本保持上下居中"></t-input>
      <t-input placeholder="无标题预设文本" />
      <t-input v-model="text3" label="未填写警告" placeholder="警告文本" :error="text3.length === 0" />
      <t-input v-model="text1" label="填写错误" error-message="提示信息" />
      <t-input v-model="text2" label="不可编辑" disabled />
    </t-cell-group>
  </div>
</template>

<script lang="ts">
import { reactive, toRefs, defineComponent } from 'vue';
import { HelpCircleFilledIcon as TIconHelpCircleFilled } from 'tdesign-icons-vue-next';

export default defineComponent({
  components: {
    TIconHelpCircleFilled,
  },
  setup() {
    const state = reactive({
      text: '',
      text1: '一段错误填写的内容',
      text2: '不可编辑的内容',
      text3: '',
    });
    const onFocus = () => {
      console.log('focus');
    };
    const onBlur = () => {
      console.log('blur');
    };
    const onChange = (val: any) => {
      console.log(val);
    };
    return {
      ...toRefs(state),
      onFocus,
      onBlur,
      onChange,
    };
  },
});
</script>
