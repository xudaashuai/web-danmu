<template>
  <div class="main vh-100">
    <top-bar title="房间"></top-bar>
    <message-list id="myData" :messages="messages"></message-list>
    <send-box @send="send"></send-box>
  </div>
</template>

<script>
  import TopBar from "./TopBar";
  import SendBox from "./SendBox";
  import MessageList from "./MessageList";
  import IO from 'socket.io-client'

  export default {
    components: {
      MessageList,
      SendBox,
      TopBar
    },
    name: 'HelloWorld',
    data() {
      return {
        messages: [],
        name: '徐大帅',
        socket: null
      }
    }, watch: {
      messages() {
      }
    },
    methods: {
      send(msg) {
        this.messages.push({
          type: 1,
          content: msg,
          name: this.name
        })
        this.socket.emit('message', {msg: msg, name: '徐大帅'})
        this.$nextTick(() => document.getElementById('myData').scrollTop = document.getElementById('myData').scrollHeight);
      }
    },
    created() {
      this.$nextTick(() => {
        this.socket = new IO('ws://118.24.24.60:3000?id=123');
        this.socket.on('message',data=>{
          this.messages.push(data)
        })
      })
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .main {
    justify-content: space-between;
    background-color: #dddddd;
  }
</style>
