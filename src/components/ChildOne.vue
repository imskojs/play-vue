<template>
<div>
  <h1>{{ title }}</h1>
  <button @click="changeTitle()">
    Change Title From Child
  </button>
</div>
</template>

<script>
export default {
  /**
   * https://vuejs.org/v2/guide/components-props.html#Prop-Validation
   */
  props: {
    title: String
  },
  methods: {
    changeTitle() {
      // Anti patent Do not change props directly. Even if this is a primitive.
      // since this is primative parent's `title` data has not changed but
      //displays child's title which may cause confusion.
      /**
       * https://vuejs.org/v2/guide/components-props.html#One-Way-Data-Flow
       */
      this.title = "From Child Title Changed";
    }
  }
};
</script>

<style scoped>
</style>


