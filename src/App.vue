<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld/>

  <Table></Table>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Table from './components/Table.vue'

export default {
  name: 'App',
  data(){
      return{


      }
  },
  components: {
    HelloWorld,
    Table,
},
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background: linear-gradient(0.25turn, #91e3ab, #ebf8e1, #91cb70b7);
}


</style>
