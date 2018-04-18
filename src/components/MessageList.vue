<template>
  <div class="main">
    <template v-for="mes in messages">
      <message-me v-if="mes.type===1" :name="mes.name" :content="mes.content">

      </message-me>
      <message-he v-if="mes.type===2" :name="mes.name" :content="mes.content">

      </message-he>
    </template>
  </div>
</template>

<script>
  import MessageMe from "./MessageMe";
  import MessageHe from "./MessageHe";

  export default {
    components: {
      MessageHe,
      MessageMe
    },
    props: ['messages'],
    name: "message-list",
    data() {
      return {}
    }
  }
</script>

<style scoped>
  .main {
    display: flex;
    flex-direction: column;
    overflow: auto;
    margin: 0;
    margin-top: 60px;
    margin-bottom: 50px;
  }
</style>
