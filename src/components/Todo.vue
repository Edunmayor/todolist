<template>
<div class="todo-container">
  <h1>Todo List</h1>
  <form @submit.prevent="addTask" class="task-form">
    <input v-model="newTask" type="text" placeholder="Add a new task" />
    <button type="submit">Add</button>
  </form>
  <ul class="task-list">
    <li v-for="(task, index) in tasks" :key="index" class="task-item">
      {{ task }}
      <button @click="removeTask(index)" class="remove-button">Remove</button>
    </li>
  </ul>
</div>
</template>

<script>
export default {
data() {
  return {
    newTask: '',
    tasks: [],
  };
},
methods: {
  addTask() {
    if (this.newTask.trim() !== '') {
      this.tasks.push(this.newTask.trim());
      this.newTask = '';
    }
  },
  removeTask(index) {
    this.tasks.splice(index, 1);
  },
},
};
</script>

<style scoped>
.todo-container {
max-width: 400px;
margin: auto;
}

.task-form {
margin-bottom: 20px;
}

.task-list {
list-style-type: none;
padding: 0;
}

.task-item {
margin-bottom: 10px;
padding: 10px;
background-color: #f0f0f0;
border-radius: 5px;
display: flex;
justify-content: space-between;
align-items: center;
}

.remove-button {
background-color: #ff5555;
color: #fff;
border: none;
padding: 5px 10px;
cursor: pointer;
}

button{
  background-color: #ff5555;
  border-radius: 5px;
  cursor: pointer;
}

html{
background-color: grey;
}
</style>