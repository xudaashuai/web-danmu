<template>
  <div class="main">
      {{content}}
  </div>
</template>

<script>
  export default {
    name: "message-tip",
    props: ['content']
  }
</script>

<style scoped>
  .main {
    max-width: 100%;
    flex-grow: 0;
    text-align: center;
    background-color: #666666;
    color: white;
    overflow-y: unset;
    padding: 0.3rem;
    border-radius: 0.3rem;
    flex-shrink: 0;
    align-self: center;
    margin-top: 5px;
  }
  .tip{

  }
</style>
