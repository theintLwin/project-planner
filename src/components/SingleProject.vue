<template>
<div class="project" :class="{complete:project.complete}" >
    <div class="flexing">
       
        <div>
            <h3 @click="showDetail=!showDetail">{{project.title}}</h3>
        </div>
        
        <div>
            <i class="fa-solid fa-trash" @click="deleteProject"></i>
            <router-link :to="{name:'EditProject', params:{id:project.id}}">
                <i class="fa-solid fa-pen"></i>
            </router-link>
            
            <i class="fa-solid fa-check" @click="completeProject"></i>
        </div>
    </div>
    <p v-if="showDetail">{{project.detail}}   
          
</p>{{project.complete}}
    </div>
 
     
 
  
</template>

<script>
export default {
    props:['project'],
    data(){
        return{
            showDetail:false,
            api:'http://localhost:3000/projects/'
            
        }
    },
    methods:{
        deleteProject(){
           // console.log("Hi");
           //fetch(api+project.id,{method:"DELETE"})
           let deleteRoute = this.api+this.project.id;
           fetch(deleteRoute,{method:"DELETE"})
           .then(()=>{
               this.$emit("delete",this.project.id)
           })
           .catch((err)=>{
               console.log(err.message());
           })
           
        },
        completeProject(){
            let updateCompleteRoute = this.api+this.project.id;
            fetch(updateCompleteRoute, {
                method:"PATCH",
                headers:{
                    "Content-Type":"application/json"
                },
                body:JSON.stringify(
                {
                    complete:!this.project.complete
                }
            )
        })
        .then(()=>{
            this.$emit("complete",this.project.id)
        })
        .catch((err)=>{
            console.log(err);
        })
        }
}
}
</script>

<style>
 .project{
     background-color:#f2f2f2;
     padding: 20px;
     margin: 10px;
     border-left:6px solid crimson;
     border-radius: 3px;
 }
 h3{
     color: indigo;
    cursor: pointer;

 }
 .flexing{
     display:flex;
     justify-content: space-between;
     align-items: center;
 }
 i{
     margin-left:15px;
    cursor: pointer;

 }
 i:hover{
     color:#777;
 }
 .complete{
     border-left-color: green;
 }
</style>