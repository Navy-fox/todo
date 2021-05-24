<template>
  <div class="todo-list">
    <div class="todo-list__header">
      <p>Description</p>
      <p>Actions</p>
    </div>
    <div class="todo-list__body">
      <div class="todo-list__item" v-for="(index,key) in tasks" :key="key" :class="index.completed?`todo-list__item--completed`:''">
        <p>{{ index.title }}</p>
        <div class="button-group">
          <v-button color="green" icon="check-fill" @click.native="checkTask(index.id)" v-if="!index.completed"/>
          <v-button color="orange" icon="check-double-fill" @click.native="checkTask(index.id)" v-if="index.completed"/>
          <v-button color="coral" icon="delete-bin-7-fill" @click.native="deleteTask(index.id)"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import VButton from "./v-button";
import axios from "axios";

export default {
  name: "todo-list",
  components: {VButton},
  data: () => ({tasks: []}),
  async created() {
    const res = await axios.get('https://jsonplaceholder.typicode.com/todos', {params: {_limit: 5}})
    this.tasks = res.data
  },
  methods: {
    deleteTask(id) {
      console.log(id)
      this.tasks = this.tasks.filter(item => item.id !== id)  //[]
    },
    checkTask(id){
      const task = this.tasks.find(item => item.id === id)
      if (task){task.completed=!task.completed}
    }
  }
}
</script>

<style scoped>

</style>