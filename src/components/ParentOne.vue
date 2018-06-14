<template>
<div>
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
  }
};
</script>

<style scoped>
</style>


