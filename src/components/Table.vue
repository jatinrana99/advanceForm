<template>
    <div class="table">
        <Input v-on:submit-item="submit" v-bind:email="email" v-bind:name="name" >
        
        </Input>
        <table class="tb">
            <tr>
            <th>Name</th>
            <th>Email</th>
            <th>Date Of Birth</th>
            </tr>

            <tr v-for="(item,index) in items" v-bind:key="index">
                <td>{{ item.name }}</td>
                <td>{{ item.email }}</td>
                <td>{{ item.dob }}</td>
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
            // editIndex:-1
        }
    },


    methods:{
        submit(email,name,dob){
            this.items.push({'email':email,
        'name':name,
        'dob':dob});
            this.email="";
            this.name="";
            this.dob="";
        }
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
    
}
th{
    border: solid 2px;
}
td{
    border: solid 2px;
    background-color: rgb(188, 188, 102);
}

</style>