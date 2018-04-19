<template>
  <div class="main">
    <template v-for="mes in messages">
      <message-me v-if="mes.type===1" :name="mes.name" :content="mes.content">

      </message-me>
      <message-he v-else-if="mes.type===2" :name="mes.name" :content="mes.content">

      </message-he>
      <message-tip v-else-if="mes.type===3" :content="mes.content">

      </message-tip>
    </template>
  </div>
</template>

<script>
  import MessageMe from "./MessageMe";
  import MessageHe from "./MessageHe";
  import MessageTip from "./MessageTip";

  export default {
    components: {
      MessageTip,
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
    overflow-y: auto;
    margin: 0;
    flex-grow: 1;
    padding-top: 65px;
    padding-bottom: 60px;
    justify-content: flex-start;
  }
</style>
