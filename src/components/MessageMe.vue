<template>
  <div class="main">
    <div class="left">
      <div class="name">
        {{name}}
      </div>
      <div class="text pv2 ph2">
        {{content}}
      </div>
    </div>
    <div class="icon bg-warning">

    </div>
  </div>
</template>

<script>
  export default {
    name: "message-me",
    props:['name','content']
  }
</script>

<style scoped>
  .main {
    padding-left: 50px;
    flex-direction: row;
    justify-content: flex-end;
    overflow: unset;
    min-height:100px;
    margin: 0;
    padding: 0.1rem;
    flex-grow: 0;flex-shrink:0;
  }
  .icon {
    height: 40px;
    width: 40px;
    min-width: 40px;
  }
  .left{
    margin-right: 5px;
    display: flex;
    flex-direction: column;
    flex-grow: 1;
    align-items: flex-end;
  }
  .text{
    background-color: #00c853;
    max-width: 80%;
    word-break: break-all;
  }
  .name{
    font-size: 0.8rem;
    padding: 0.1rem;
    background-color: white;
    border-radius: 10%;
    align-self: flex-end;
  }
</style>
