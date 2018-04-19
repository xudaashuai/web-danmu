<template>
  <div class="main vh-100">
    <top-bar title="房间"></top-bar>
    <message-list id="myData" class="row" :messages="messages"></message-list>
    <send-box @send="send"></send-box>
    <van-popup
        class="pv2 ph2"
        v-model="show"
        :close-on-click-overlay="false"
    >
      <van-field
          v-model="name"
          placeholder="请输入昵称"
      />
      <van-button class="mt2" type="primary" size="large" @click="confirm">确定</van-button>

    </van-popup>
  </div>
</template>

<script>
  import TopBar from "./TopBar";
  import SendBox from "./SendBox";
  import MessageList from "./MessageList";
  import IO from 'socket.io-client'
  import {Dialog} from 'vant';
  import {Toast} from 'vant';

  export default {
    components: {
      MessageList,
      SendBox,
      TopBar
    },
    name: 'HelloWorld',
    data() {
      return {
        messages: [
          {
            type: 3,
            content: '2131223',
          }
        ],
        name: '',
        socket: null,
        show: true
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
      },
      setName() {
      },
      confirm() {
        if (!this.name) {
          Toast.fail('名字哦');
        }
        else {
          this.socket = new IO(`ws://118.24.24.60?id=123&name=${encodeURI(this.name)}`);
          this.socket.on('message', data => {
            console.log(data)
            this.messages.push({
              content: data.msg,
              name: '徐小帅',
              type: 2
            })
            this.$nextTick(() => document.getElementById('myData').scrollTop = document.getElementById('myData').scrollHeight);
          })
          this.socket.on('join', data => {
            console.log(data)
            this.messages.push({
              content: data.msg,
              type: 3
            })
            this.$nextTick(() => document.getElementById('myData').scrollTop = document.getElementById('myData').scrollHeight);
          })
          Toast.success('ojbk');
          this.show = false
        }
      },
    },
    created() {
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .main {
    justify-content: space-between;
    background-color: #dddddd;
    display: flex;
    overflow: hidden;
  }

  .pop {
    padding: 20px;
  }
</style>
