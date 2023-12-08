<template >
  <div id="app">
  <work v-bind:works="works" @remove-all-works="removeAllWorks" @add-work="addWork"></work>
</div> 
</template>

<script>
import work from './components/work';

export default {
  name: 'App',
  components: {
    work,
  },
  data(){
    return{
      works:[
        {
        id:1,
        title:'Playing cricket',
        status:true,
        },
        {
        id:2,
        title:'Watching TV',
        status:false,
        },
        {
        id:3,
        title:'Chat with friends',
        status:false,
        },
      ]
    }
  },
  methods:{
    addWork(newWork) {
      this.works.push(newWork);
    },
    removeAllWorks() {
      this.works = []; // Update the works data
    },
    
  }
}
</script>

<style>

</style>
