<template>

  <nav class="filter-nav">
      <button @click="filterBy('all')" :class="{active:current==='all'}">all</button>
      <button @click="filterBy('complete')" :class="{active:current==='complete'}">complete</button>
      <button @click="filterBy('ongoing')" :class="{active:current==='ongoing'}">ongoing</button>
  </nav>
 
</template>

<script>
export default {
    methods:{
        filterBy(value){
           // console.log(value)
           this.$emit('filterValue',value);
        }
    },
    props:['current']
}
</script>

<style>
    .filter-nav button{
        letter-spacing: 1px;
        margin-right:10px;
        font-weight: bold;
        cursor:pointer;
        text-transform:uppercase;
        background:none;
        border:none;
        color:#bbb;
        outline:none;
        font-size: 12px;
    }
    
     button.active {
        color: #333;
    }
    
</style>