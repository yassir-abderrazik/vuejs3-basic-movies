<template lang="">
  <div class="w-full mt-10 p-10 bg-gray-800">
    <p class="text-white">COPYRIGHTS 2021</p>
    <a :href="url">click here</a>
  </div>
</template>
<script>
export default {
  props: ["url", "text", "title"],
};
</script>
<style lang=""></style>
