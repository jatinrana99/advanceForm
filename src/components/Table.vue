<template>
    <div class="table">
        <Input v-on:submit-item="submit" v-bind:editEmail="editEmail" v-bind:edit-index="editIndex"
        v-bind:editName="editName" v-bind:Dob="editDob" 
                v-on:edit-item="edit">
        
        </Input>
        <table class="tb">
            <tr>
                <th v-for="(item,index) in columns" v-bind:key="index" v-on:click="sortData(index)">{{ item }} ⇅</th>
            <!-- <th>Name</th>
            <th>Email</th>
            <th>Date Of Birth</th> -->
            <th>Edit</th>
            <th>Delete</th>
            </tr>

            <tr v-for="(item,index) in items" v-bind:key="index">
                <td v-for="(rowitem,rowindex) in item" v-bind:key="rowindex">{{ rowitem }}</td>
                <!-- <td>{{ item.name }}</td>
                <td>{{ item.email }}</td>
                <td>{{ item.dob }}</td>   -->
                <!-- <td>{{ item.password }}</td> -->
                <td>
                    <i class="fa-solid fa-pen-to-square" v-on:click.prevent="editItem(index)"></i>
                </td>
                <td>
                    <i class="fa-solid fa-trash" v-on:click.prevent="deleteItem(index)"></i>
                </td>

            </tr>
            
        </table>
    </div>
</template>

<script>

import Input from './Input.vue'

export default {
    name:`Table`,
    components:{
        Input
    },
    data(){
        return{
            items:[],
            editEmail:"",
            editDob:"",
            editName:"",
            editIndex:-1,
            columns:["Email","Name","DOB"],
            sortDesc:false,
            sortKey:""


        }
    },


    methods:{
        submit:function(editEmail,editName,editDob){
            this.items.push({'email':editEmail,
                             'name':editName,
                             'dob':editDob
                            });
            this.email="";
            this.name="";
            this.dob="";
        },
        editItem:function(index){
            console.log("edit index");
            this.editIndex= index;
            // this.name = this.items[index];4
            this.editEmail = this.items[index];

    },

    edit:function(obj){
            var{editEmail,editName,editDob,editIndex} = obj;

            console.log("hello from edit");

            this.items[editIndex].email=editEmail;
            this.items[editIndex].name=editName;
            this.items[editIndex].dob=editDob;
            


            // this.name="";
            // this.email="";
            // this.dob="";
            // this.editIndex =-1;


            this.editName="";
            this.editEmail="";
            this.editDob="";
            this.editIndex =-1;


        },

    deleteItem: function(index) {
        this.items.splice(index,1);
    },

    sortData(index){
        console.log("Hello from sortTableData");
      const key = this.columns[index].toLowerCase().replace(" ","_");
      console.warn(key);
      if(this.sortKey == key){
        this.sortDesc =! this.sortDesc;
      }
      else{
        this.sortKey = key;
        this.sortDesc = false;
      }
      console.warn("check" , this.sortKey=='dob');

      this.items.sort((a,b) =>{
        const valueA = a[this.sortKey];
        const valueB = b[this.sortKey];
        if(this.sortKey == "dob"){
            // convert the date string to date objects
            const dateA = new Date(valueA);
            const dateB = new Date(valueB);
            if(this.sortDesc){
                return dateB.getTime() - dateA.getTime();
            }
            else {
                return dateA.getTime() - dateB.getTime();
            }
        }
        else {
            if(this.sortDesc){
                return valueB.localeCompare(valueA);
            }
            else {
                return valueA.localeCompare(valueB);
            }
        }
      });
    },
    
  
  }
}
</script>

<style scoped>
.tb{
    border:2px soild;
}


table{
    border : solid brown;
    position: absolute;
    width: 1045px;
    left: 170px;
    top: 80%;
}
th{
    border: solid 2px;
}
td{
    border: solid 2px;
    background-color: rgb(188, 188, 102);
}

</style>