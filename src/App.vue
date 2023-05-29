<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld/>
  <Form>
    <template v-slot:header>
      <h1>Registration Form</h1>
    </template>
    <template v-slot:body >
      <div id="body">
      <label for="email">Email</label> <input type="email" id="email">
      <label for="name">Name</label> <input type="text" id="name">
      <label for="dob">Date Of Birth</label> <input type="date" id="dob">
      <label for="password">Password</label> <input type="password" id="password">
      <label for="conformPassword">Conform Password</label> <input type="password" id="conformPassword">
      <div>
        <label for="teamAndcondition">Terms and conditions</label> <input type="checkbox" id="termAndCondition">
      </div>

      </div>
      
    </template>
    <template v-slot:footer>
      <button id="button">Submit Form</button>
    </template>
  </Form>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Form from './components/Form.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    Form
  }
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
}

#body{
  display: flex;
  flex-direction: column;
  margin: 3px;
  padding: 5px;
  text-align: left;
}


#body input{
  margin:3px;
}

.lab{
  text-align: left;
}

#button{
  margin: 5px;
}
</style>
