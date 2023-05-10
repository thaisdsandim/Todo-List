<template>
  <div id="list">
    <h2>{{ title }}</h2>
    <form @submit.prevent="addTask">
      <input type="text" v-model="newTask" placeholder="Escreva a sua tarefa...">
      <button type="submit">Adicionar</button>
    </form>
    <h3>A Fazer:</h3>
    <ul>
      <li v-for="(task, index) in tasks" :key="index">
        <label>
        <button @click="completed(index)" class="button check"><i class="fa-solid fa-check"></i></button>
        <button @click="deleteTask (index)" class="button delete"><i class="fa-solid fa-trash"></i></button>
        {{ task.text }}
        </label>
      </li>
    </ul>
    <h3>Feitas:</h3>
    <ul v-if="completedTasks.length > 0">
      <li v-for="(task, index) in completedTasks" :key="index">
        <label>
        <button @click="returnTask(index)" class="button"><i class="fa-solid fa-xmark"></i></button>
        <span>{{ task.text }}</span>
        </label>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    title: String
  },
  data() {
    return {
      tasks: [],
      completedTasks: [],
      newTask: ''
    }
  },
  methods: {
    addTask() {
      if (this.newTask.trim() !== '') {
        this.tasks.push({ text: this.newTask, completed: false })
        this.newTask = ''
      }
    },
    deleteTask(index) {
      this.tasks.splice(index, 1)
    },
    completed(index) {
      const completedTask = this.tasks.splice(index, 1)[0]
      completedTask.completed = true
      this.completedTasks.push(completedTask)
    },
    returnTask(index) {
      const returnedTask = this.completedTasks.splice(index, 1)[0]
      returnedTask.completed = false
      this.tasks.push(returnedTask)
    }
  }
}
</script>

<style>
i{
  font-size: 10px;
}
ul{
  text-align: start;
}
span{
  padding-left: 5px;
  padding-right: 5px;
  text-decoration: line-through;
}
.button{
  padding: 1px;
  padding-left: 4px;
  padding-right: 4px;
  margin-bottom: 0;
  margin-left: 0;
}
.check{
background-color: rgba(255, 255, 255, 0.623);
}
.delete{
  background-color: rgba(255, 0, 0, 0.473);
}
</style>