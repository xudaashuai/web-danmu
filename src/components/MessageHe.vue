<template>
  <div class="main">
    <div class="icon bg-warning">

    </div>
    <div class="right">
      <div class="name">
        {{name}}
      </div>
      <div class="text bg-white pv2 ph2">
        {{content}}
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "message-he",
    props: ['name', 'content']
  }
</script>

<style scoped>
  .main {
    padding-right: 50px;
    max-width: 100%;
    flex-direction: row;
    justify-content: flex-start;
    overflow: unset;
    min-height: 100px;
    margin: 0;
    padding: 0.1rem;
    flex-grow: 0;flex-shrink:0;
  }

  .icon {
    height: 40px;
    min-width: 40px;
    margin: 0.5em 0;
  }

  .right {
    margin: 0 0 0 5px;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    flex-grow: 1;
    align-self: flex-start;
  }
.text{
  word-break: break-all;
  max-width: 80%;
}
  .name {
    font-size: 0.8rem;
    padding: 0.1rem;
    background-color: white;
    border-radius: 10%;
  }
</style>
