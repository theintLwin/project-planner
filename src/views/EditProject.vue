<template>
  <h1>Edit Project </h1>
  <form @submit.prevent = "addProject">
      <label>Project Title</label>
      <input type="text" v-model = "title">
      <label>Project Description</label>
      <input type="text" v-model="detail">
      <button>Update Project</button>
  </form>
</template>

<script>
export default {
    props:['id'],
    data(){
      return {
        title:"",
        detail:""
      }
    },
    mounted(){
      fetch('http://localhost:3000/projects/'+this.id)
      .then((res)=>{
        return res.json();
      })
      .then((data)=>{
        this.title=data.title;
        this.detail=data.detail;
      })
      .catch((err)=>{
        console.log(err);
      })
    }
}
</script>

<style>

</style>