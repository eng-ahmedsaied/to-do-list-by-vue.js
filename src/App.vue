<template>
  <div id="app">
    <Task v-bind:tasks="tasks" />
  </div>
</template>

<script>
import Task from "./components/Task.vue"; 

export default {
  name: "App",
  components: {
    Task,
  },
  data() {
    return {
      tasks: [
        { id: 1, title: "learn vue js", completed: true },
        { id: 2, title: "watch netflix", completed: true },
        { id: 3, title: "go shopping", completed: true }, 
        { id: 4, title: "learn guitar", completed: true }, 
        { id: 5, title: "making beats", completed: false }, 

      ],
    };
  },
};
</script>





<style lang="scss">

.toggle {
    background-color: #f9f9f9;
    border: none;
    font-size: 16px;
    padding: 10px;
    cursor: pointer;
    text-align: left;
    width: 100%;
    transition: all 0.3s ease;
  }
  
  .toggle:hover {
    background-color: #e0e0e0;
  }
  
  .toggle-completed {
    text-decoration: line-through;
    color: #999;
  }

body {
  margin: 0;
  padding: 0;
  background-color: #5ecfcf;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.container {
  display: flex;
  justify-content: center;
  padding: 40px 20px;
}

.task {
  background: #ffffff;
  padding: 30px;
  border-radius: 15px;
  width: 100%;
  max-width: 500px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
}

.title h2 {
  text-align: center;
  color: #333;
  margin-bottom: 20px;
}

.form {
  display: flex;
  justify-content: space-between;
  gap: 10px;
  margin-bottom: 20px;
}

.form input {
  flex: 1;
  padding: 10px 15px;
  border: 1px solid #ccc;
  border-radius: 10px;
  font-size: 16px;
}

.form button {
  padding: 10px 20px;
  background-color: #5ecfcf;
  border: none;
  border-radius: 10px;
  color: white;
  font-size: 18px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.form button:hover {
  background-color: #4bb7b7;
}

.taskItems ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.clearBtns {
  display: flex;
  justify-content: space-between;
  margin-top: 20px;
}

.clearBtns button {
  padding: 10px 15px;
  border: none;
  border-radius: 8px;
  background-color: #ff6b6b;
  color: white;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.clearBtns button:hover {
  background-color: #e25e5e;
}

.pendingTasks {
  margin-top: 15px;
  text-align: center;
  font-weight: bold;
  color: #333;
}

  
</style>
