<template>
  <div>
    <h1>Lista de Tarefas</h1>
    <form @submit.prevent="addList">
      <input type="text" v-model="newListTitle" id="inputList" placeholder="Nomeie a sua lista...">
      <button type="submit">Criar Lista</button>
    </form>
    <div id="lists">
      <div v-for="(list, index) in lists" :key="index" id="listCard">
        <List :title="list.title" />
      </div>
    </div>
  </div>
</template>
  
<script>
import List from './List.vue'
  
export default {
  components: {
    List
  },
  data() {
    return {
      lists: [],
      newListTitle: ''
    }
  },
  methods: {
    addList() {
      if (this.newListTitle.trim() !== '') {
        this.lists.push({
          title: this.newListTitle,
          tasks: []
        })
        this.newListTitle = ''
      }
    },
    addTaskToList(listIndex, task) {
      this.lists[listIndex].tasks.push(task)
    }
  }
}
</script>

<style>
div{
  align-content: center;
}
h1{
  margin-top: 20px;
  margin-bottom: 20px;
}
#inputList{
  background-color: rgba(255, 255, 255, 0.623);
}
#lists{
  display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
}
#listCard{
  background-color: rgba(255, 255, 255, 0.623);
  max-width: 400px;
  margin-top: 20px;
  border-radius: 10px;
  padding: 15px;
}
</style>