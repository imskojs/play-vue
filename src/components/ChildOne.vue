<template>
<div>
  <h1>{{ title }}</h1>

</div>
</template>

<script>
export default {
  /**
   * https://vuejs.org/v2/guide/components-props.html#Prop-Validation
   */
  props: {
    title: String
  }
};
</script>

<style scoped>
</style>


