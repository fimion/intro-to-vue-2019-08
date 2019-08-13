<template>
  <div id="app">
    <label>
      <input type="checkbox"
             v-model="showComplete">
      Show Complete
    </label>
    <div >
      <h1>Alex's To-Do List</h1>
      <ul v-if="showComplete">
        <li v-for="item in finishedToDoItems"
            :key="'TODO'+item.id">
          <to-do-item :item="item"
                      @update-item="updateItem"></to-do-item>
        </li>
      </ul>
      <ul v-else>
        <li v-for="item in unfinishedToDoItems"
            :key="'TODO'+item.id">
          <to-do-item :item="item"
                      @update-item="updateItem"></to-do-item>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import ToDoItem from './components/ToDoItem.vue'

export default {
  name: 'app',
  components:{
    ToDoItem,
  },
  data(){
    return {
      // Do we want to see our completed todos?
      showComplete:false,
      // Our Illustrious To Do List
      toDoList:[
        {
          id:1,
          title:"Mow Lawn",
          description: "It's kinda shabby looking.",
          complete:false,
        },
        {
          id:2,
          title:"Take out the trash",
          description: "Seriously. What is that smell?",
          complete:false,
        },
        {
          id:3,
          title:"Take a nap.",
          description: "You seem tired.",
          complete:false,
        },
      ],
    }
  },
  methods:{
    updateItem(item){
      this.toDoList.forEach((el, i) => {
        if(el.id === item.id){
          this.$set(this.toDoList, i,item);
        }
      });
    },
  },
  computed:{
    unfinishedToDoItems(){
      return this.toDoList.filter(e=>!e.complete)
    },
    finishedToDoItems(){
      return this.toDoList.filter(e=>e.complete)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
