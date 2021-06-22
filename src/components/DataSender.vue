<template>
  <button @click="sendData">Send Data</button>
</template>

<script>
export default {
  name: 'DataSender',
  // emits:['sending-start','sending-complete'],
  emits: { // defining the value of the emits
    'sending-complete'(payload) {
      if (typeof payload.duration === 'number' && payload.response) {
        return true
      } else {
        return false
      }
    },'sending-start': null
  },

  methods: {
    sendData() {
      this.$emit('sending-start');

      // send data to API

      this.$emit('sending-complete',{
        duration: 2,
        response: 'hello i am response'
      })
    }
  }
}
</script>
