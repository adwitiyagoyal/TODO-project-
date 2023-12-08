<template>
    <div class="main">

      <div>
        <h1><strong>TO-DO List</strong> </h1>
      </div> 

      <br>

      <div>
        <input placeholder="Add work" v-model="newWork"  @keyup.enter="addWork">
      </div>

      <br>

      <div class="items">
        <ul type="none" >
            <li v-for="work in works" :key="work.id">
                <button :class="{ 'completed': work.status }" @click="toggleCompleted(work)"> {{ work.title }} </button>   
            </li>
        </ul>
      </div>

      <div>
      <br>
      <button class="clear" @click="removeAll"> Clear All</button>
      </div>

    </div>
    
</template>

<script>
    export default {
        name,
        props: ['works'],
        data(){
            return{
                newWork:''
            }
        }, 
        methods:{
            addWork(){
                if(this.newWork){
                    this.$emit('add-work',{
                        title:this.newWork,
                        status:false
                    });
                    this.newWork='';
                }
            },
            removeAll(){
                this.$emit('remove-all-works');
            },
            toggleCompleted(work) {
                // Toggle the 'status' property of the work item
                work.status = !work.status;
            },
            
            

        }
    }
</script>

<style scoped>
.completed {
  text-decoration: line-through;
}

</style>