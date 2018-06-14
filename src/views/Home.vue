<template>
<div class="home">
  <parent-one></parent-one>
  <!-- <hello-world></hello-world> -->
</div>
</template>

<script>
import HelloWorld from "@/components/HelloWorld";
import ParentOne from "@/components/ParentOne";
export default {
  components: {
    HelloWorld,
    ParentOne
  }
};
</script>
