<template>
<div class="project" >
    <div class="flexing">
       
        <div>
            <h3 @click="showDetail=!showDetail">{{project.title}}</h3>
        </div>
        
        <div>
            <i class="fa-solid fa-trash"></i>
            <i class="fa-solid fa-pen"></i>
            <i class="fa-solid fa-check"></i>
        </div>
    </div>
    <p v-if="showDetail">{{project.detail}}</p>
    </div>
 
     
 
  
</template>

<script>
export default {
    props:['project'],
    data(){
        return{
            showDetail:false
        }
    },
    methods:{
   
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
</style>