<template>
  <el-button
    class="nm-button"
    :type="type"
    :size="getSize"
    :plain="plain"
    :round="round"
    :circle="circle"
    :loading="loading"
    :disabled="disabled"
    :autofocus="autofocus"
    :native-type="nativeType"
    @click="$emit('click')"
  >
    <nm-icon v-if="!loading&&icon" :name="icon"/>
    <slot>
      <span v-if="!circle&&text" class="nm-button-text" v-html="text"/>
    </slot>
  </el-button>
</template>
<script>
export default {
  name: 'Button',
  props: {
    /** 尺寸，默认或者为空时，按照皮肤的字号设置 */
    size: String,
    /** 类型 primary/success/warning/danger/info/text */
    type: String,
    /** 是否朴素按钮 */
    plain: Boolean,
    /** 是否圆角按钮 */
    round: Boolean,
    /** 是否圆形按钮 */
    circle: Boolean,
    /** 是否加载中状态 */
    loading: Boolean,
    /** 是否禁用状态 */
    disabled: Boolean,
    /** 图标 */
    icon: String,
    /** 是否默认聚焦 */
    autofocus: Boolean,
    /** 原生 type 属性 button/submit/reset */
    nativeType: String,
    // 文本
    text: String
  },
  computed: {
    getSize () {
      return this.size || this.fontSize
    }
  }
}
</script>
