
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
    <button id="button" v-on:click.prevent="submit" >Submit Form</button>
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
    data(){
      return{
        email:"",
        name:"",
        dob:""
      }
    },
    props:{
        // email:{}
        editEmail:{type:String,require:true},
        editIndex:{type:Number,require:true}
    },

    
    watch: {
            editEmail(newEmail){
                console.log("watch", newEmail.email , newEmail.name , newEmail.dob);
                this.email=newEmail.email;
                this.name=newEmail.name;
                this.dob=newEmail.dob;
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