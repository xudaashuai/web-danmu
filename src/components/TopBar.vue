<template>
  <div class="bg-info pv1 row">
    <div class="title tc white">
      {{title}}
    </div>
  </div>
</template>

<script>
  export default {
    name: "top-bar",
    props: ['title']
  }
</script>

<style scoped>
  .title{
    font-size: 2rem;
  }
  .row{
    position: fixed;
    top:0;
  }
</style>
