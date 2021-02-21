<template>
  <div id="app">
    <h1>To-Do List</h1>
    <to-do-form @todo-added="addToDo"></to-do-form>
     <ul>
      <li v-for="goblin in ToDoItems" :key="goblin.id">
       <to-do-item :label="goblin.label" :done="goblin.done" :id="goblin.id"></to-do-item>
      </li>
     </ul>
  </div>
</template>

<script>
  import uniqueId from 'lodash.uniqueid';
  import ToDoItem from './components/Sleestak.vue';
  import ToDoForm from './components/ToDoForm.vue';
  export default {
    name: 'App',
    components: {
      ToDoItem,
      ToDoForm
    },
    data() {
      return {
        ToDoItems: [
          { id: uniqueId('todo-'), label: 'Eat lunch', done: true },
          { id: uniqueId('todo-'), label: 'Solve a myster', done: false },
          { id: uniqueId('todo-'), label: 'Narfle the Garthok', done: false}
        ]
      };
    },
    methods :{
      addToDo(toDoLabel) {
        console.log('ToDoAdded: ', toDoLabel);
        this.ToDoItems.push({id:uniqueId('todo-'), label: toDoLabel, done: false});
      }
    }
  };
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;

}
ul {
  list-style-type: none;
}
</style>
