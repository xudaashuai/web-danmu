<template>
  <div class="row main bg-accent">
    <input v-model="mes" class="card " type="text" @keyup.enter="send">
    <button :disabled="mes===''" class="btn primary" @click="send">发送</button>
  </div>
</template>

<script>
  export default {
    name: "send-box",
    data() {
      return {
        mes: ''
      }
    },
    methods: {
      send() {
        if (this.mes) {
          this.$emit('send', this.mes)
          this.mes=''
        }
      }
    }
  }
</script>

<style scoped>
  .main {
    display: flex;
    position: fixed;
    left: 0;
    bottom: 0;
    flex-direction: row;
    align-items: center;
    background-color: #eeeeee;
  }

  .card {
    flex-grow: 1;
  }

  .row {
    margin: 0;
  }
</style>
