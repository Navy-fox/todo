<template>
  <div class="todo-list">
    <div class="todo__input">
      <input class="input" type="text" v-model="title" placeholder="Add new task">
      <v-button @click.native="addTask"/>
    </div>
    <div class="todo-list__header">
      <p>Description</p>
      <p>Actions</p>
    </div>
    <div class="todo-list__body">
      <div class="todo-list__item" v-for="(index,key) in tasks" :key="key"
           :class="index.completed?`todo-list__item--completed`:''">
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
  data: () => ({
    tasks: [],
    title: '',
  }),
  props: {
    userId: {
      type: Number,
      required: true
    }
  },
  async created() {
    const res = await axios.get('https://jsonplaceholder.typicode.com/todos', {params: {userId: this.userId}})
    this.tasks = res.data
  },
  methods: {
    deleteTask(id) {
      console.log(id)
      this.tasks = this.tasks.filter(item => item.id !== id)  //[]
    },
    checkTask(id) {
      const task = this.tasks.find(item => item.id === id)
      if (task) {
        task.completed = !task.completed
      }
    },
    addTask() {
      const objectTask = {
        completed: false,
        id: this.tasks.length + 100,
        title: this.title,
        userId: 1
      }
      //Добавить объект в массив this.tasks
      this.tasks.push(objectTask)
      this.title = ''
    }
  }
}
</script>

<style scoped>

</style>