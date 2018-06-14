<template>
<div>
  <button @click="changeTitle()">
    Change Title From Parent
  </button>
  <child-one :title="title"></child-one>
</div>
</template>

<script>
import ChildOne from "@/components/ChildOne";
export default {
  components: {
    ChildOne
  },
  data() {
    return {
      title: "Passed Down From Parent One"
    };
  },
  methods: {
    changeTitle() {
      this.title = "From Parent Title Changed";
    }
  }
};
</script>

<style scoped>
</style>


