<template>
    <div class="container">
      <div class="task">
        <div class="title">
          <h2>TO DO LIST</h2>
        </div>
  
        <div class="form">
          <input type="text" placeholder="new task" v-model="newTask" @keyup.enter="addTask" />
          <button @click="addTask"><i class="fas fa-plus"></i></button>
        </div>
  
        <div class="taskItems">
          <ul>
            <TaskItems v-bind:task="task" v-for="(task,index ) in localTasks" :key="task.id" 
            @remove="removeTask(index)"
            @complete=" completeTask(task)">

            </TaskItems>

          </ul>
        </div>
  
        <div class="clearBtns">
          <button @click="clearCompleted">Clear Completed</button>
          <button @click="clearAll">Clear All</button>
        </div>
  
        <div class="pendingTasks">
          <span>Pending Tasks: {{ inComplete }}</span>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import TaskItems from"./Task-items.vue"
  export default {
    name: "TaskComponent",
    props: ["tasks"],
    components:{
        TaskItems
    },
    data() {
      return {
        newTask:"",
        localTasks: [...this.tasks],
      };
    },
    computed: {
      inComplete() {
        return this.localTasks.filter(this.inProgress).length;
      },
    },
    methods: {
        addTask(){
            if (this.newTask){
                this.localTasks.push({id: Date.now(),
                    title:this.newTask
                    ,completed:false});
                this.newTask="";
            }
        },

      inProgress(task) {
        return !this.isCompleted(task);
      },
      isCompleted(task) {
        return task.completed;
      },
      clearCompleted() {
        this.localTasks = this.localTasks.filter(this.inProgress);
      },
      clearAll() {
        this.localTasks = [];
      },
      removeTask(index){
        this.localTasks.splice( index , 1 );
      },
      completeTask(task){
        task.completed=!task.completed;
      }
    },
  };
  </script>
  