
<template>

<button v-on:click="()=>TogglePopup('buttonTrigger')" class="register">Register</button>
<br>
<br>
<br>
<Pop v-if="popupTriggers.buttonTrigger" :TogglePopup="
()=>TogglePopup('buttonTrigger')">

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

    <!-- <div>
      <button v-on:click="arrange()">Sort A table</button>
      <button type="button" @click="showModel=true">Launch</button>
      <button v-on:click="handleAlertClick">Alert</button>
      <button v-on:click="handlePromptClick">Prompt Dialog</button>
    </div> -->

    </div>
    
  </template>
  <template v-slot:footer>
    <button id="button" v-on:click.prevent="submit"  v-on:click="handleSuccessClick()">Submit Form</button>

  </template>



    </Form>
  </Pop>

</template>

<script>

import Form from './Form.vue'
import Swal from 'sweetalert2'
import Pop from  './Pop.vue'
import {ref} from 'vue'
export default {
    name:`Input`,
    components:{
        Form,
        Pop
    },
    data(){
      const popupTriggers = ref({
        buttonTrigger:false,
        timedTrigger:false
      });

      const TogglePopup=(trigger)=>{
        popupTriggers.value[trigger] =! popupTriggers.value[trigger]
      };
      return{
        email:"",
        name:"",
        dob:"",
        Pop,
        popupTriggers,
        TogglePopup,
      }
    },
    props:{
        // email:{}
        editEmail:{type:String,require:true},
        editIndex:{type:Number,require:true},
        editName:{type:String,require:true},
        editDob:{type:String,require}
    },

    
    watch: {
            editEmail(newEmail){
                console.log("watch", newEmail.email , newEmail.name , newEmail.dob);
                this.email=newEmail.email;
                this.name=newEmail.name;
                this.dob=newEmail.dob;
                console.log(newEmail.email);
            // },
            // editName(newName){
            //     console.log("watch", newName.name);
            //     this.name=newName.name;
            // },
            // editPassword(newPassword){
            //     console.log("watch",  newPassword.password);
            //     this.password=newPassword.password;
            // }
            }
        },
    methods:{
      submit:function(){
            

             if(this.editIndex !== -1){

            this.$emit("edit-item", {
                editEmail:this.email,
                editName:this.name,
                editDob:this.dob,
                editIndex:this.editIndex
            });}
            else{
            this.$emit("submit-item", this.email, this.name , this.dob);
        }
            this.email="";
            this.name="";
            this.dob="";
            // eslist-disable the next line

        
        },

        arrange(){
          console.log("arrange");
          return alert ("arrange");
        },

        handleAlertClick(){
          Swal.fire("This is a simple alert ")
        },
        handlePromptClick(){
          Swal.fire({
            title:"Enter your name ",
            input:'text',
            inputLabel:'Name',
            inputPlaceholder:'Enter Your Name',
            showCancelButton:true,
            inputValidator:(value)=>{
              if(!value){
                return 'you need  to enter a name!'
              }
            }
          }).then((result)=>{
            if(result.isConfirmed){
              Swal.fire('Hello ${result.value}!');
            }
          });
        },
        handleSuccessClick(){
          Swal.fire('Success!','Your action has been completed.' , 'success');
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

.register{
  font-weight: 500;
  font-size: 30px;
  border: 2px solid #41b883;
  background-color: #35495e;
  color:#41b883;
  padding: 27px;
  border-radius: 15%;
}
</style>