<template>
  <div class="about">
    <h1>Profile id: {{$route.params.id}}</h1>
    <todo-list :user-id="Number($route.params.id)"></todo-list>
  </div>
</template>
<script>
import TodoList from "../components/todo-list";
export default {
  components: {TodoList}
}
</script>