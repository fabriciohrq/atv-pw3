<template>
  <div id="app">
    <h1>Tarefas</h1>
    <NewTask @taskAdded="adddTask"/>
    <AddTask
     :tasks="tasks"
     @taskDeleted="deleteTask"
     @taskStateChanged="toggleTaskState"
     />    
  </div>
</template>

<script>
import AddTask from './components/AddTask.vue';
import NewTask from './components/NewTask.vue';
export default {
  components: {
    AddTask,
    NewTask
  },
  data(){
    return{
      tasks: [{
        name: 'Lavar louça',
        pending: true
      },
      {
        name: 'Lavar roupa',
        pending: false
      },
      ]
    }
  },
  methods: {
    adddTask(task){
      const sameName = t => t.name === task.name
      const reallyNew = this.tasks.filter(sameName).length == 0;

      if(reallyNew){
        this.tasks.push({
          name: task.name,
          pending: true
        });
      }
    },
    deleteTask(index){
      this.tasks.splice(index, 1);
    },
    toggleTaskState(index){
      this.tasks[index].pending = !this.tasks[index].pending
    }
  }
}
</script>

<style>
  body{
    font-family: 'Lato', sans-serif;
    background: linear-gradient(to right, rgb(22, 34, 42), rgb(58, 96, 115));
    color: whitesmoke;
  }

  #app{
    display: flex;
    flex: 1;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 100vh;
  }

  #app h1{
    margin-bottom: 5px;
    font-weight: 300;
    font-size: 3rem;
  }
</style>