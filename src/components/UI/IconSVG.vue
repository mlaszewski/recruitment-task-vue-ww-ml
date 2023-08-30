<template>
  <img
      :src="`../../assets/icons/${iconName}.svg`"
      class="icon"
  />
  <svg
      viewBox="0 0 24 24"
      class="icon"
      :class="$options.methods.getStyleClasses(props)"
      v-bind="data.attrs"
      v-on="listeners"
      role="img"
  >
    <title>{{ props.title || props.name }}</title>
    <desc v-if="props.desc">{{ props.desc }}</desc>
    <path :d="$options.methods.getPath(props)" />
  </svg>
</template>

<script>
export default {
  props: ['iconName']
}
</script>

<style lang="scss">
.icon {
  min-height: 28px;
  height: 100%;
  min-width: 28px;
  width: 100%;
}
</style>