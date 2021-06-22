<template>
  <div class="hello">
    <button @click="showMessage = !showMessage">Toggle Message in Teleport</button>
    <button @click="showModal = true">Show Modal</button>
    <teleport to="#purple-box">
      <p v-if="showMessage">Hello from HelloWorld</p>
    </teleport>
    <DataSender @sending-start="started" @sending-complete="completed" />
    <SomeButtons/>
  </div>
  <teleport to="#modal-container">
    <AppModal v-if="showModal">
      <h1>Hi Hesham</h1>
      <button @click="showModal = false">Close</button>
    </AppModal>
  </teleport>
</template>

<script>
import SomeButtons from "@/components/SomeButtons";
import DataSender from "@/components/DataSender";
import AppModal from "@/components/AppModal";
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  components:{
    SomeButtons,
    DataSender,
    AppModal
  },
  data(){
    return {
      showMessage: true,
      showModal: false
    }
  },
  methods: {
    started() {
      console.log('🟢 Started')
    },
    completed() {
      console.log('🏁 Completed')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
