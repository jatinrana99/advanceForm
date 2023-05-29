
<template>
    <Form>
        <template v-slot:header>
    <h1>Registration Form</h1>
  </template>
  <template v-slot:body >
    <div id="body">
    <label for="email">Email</label> <input type="email" id="email" v-model="email">
    <label for="name">Name</label> <input type="text" id="name" v-model="name">
    <label for="dob">Date Of Birth</label> <input type="date" id="dob" v-model="dob">
    <label for="password">Password</label> <input type="password" id="password" v-model="password">
    <label for="conformPassword">Conform Password</label> <input type="password" id="conformPassword" v-model="conformPassword">
    <div>
      <label for="teamAndCondition">Terms and conditions</label> <input type="checkbox" id="termAndCondition">
    </div>

    </div>
    
  </template>
  <template v-slot:footer>
    <button id="button" v-on:click.prevent="submit()" >Submit Form</button>
  </template>



    </Form>
</template>

<script>
import Form from './Form.vue'
export default {
    name:`Input`,

    components:{
        Form
    },
    methods:{
        submit(){
            this.$emit("submit-item", this.email, this.name , this.dob);
            this.email="";
            this.name="";
            this.dob="";
        }
    }
}
</script>


<style scoped>
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
  height: 57px;
background-color: chocolate;
border-radius: 34%;
}
</style>