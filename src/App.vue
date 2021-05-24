<template>
  <div class="todo">
    <div class="wrapper">
      <div class="todo__input">
        <input class="input" type="text" placeholder="Add new task">
        <v-button/>
      </div>
      <todo-list></todo-list>
    </div>
  </div>
</template>

<script>

import TodoList from "./components/todo-list";
import VButton from "./components/v-button";

export default {
  name: 'App',
  components: {VButton, TodoList}
}
</script>

<style lang="scss">
.input {
  padding-left: 10px;
  border-width: 1px;
  width: 500px;
  border-radius: 5px;
  border-style: solid;
  border-color: #BDBDBD;
  outline: none;
}


.wrapper {
  max-width: 1440px;
  margin: 0 auto;
}

.button-group {
  display: grid;
  grid-auto-columns: min-content;
  grid-auto-flow: column;
  grid-column-gap: 10px;
}

.todo {
  padding: 20px;

  &__input {
    display: flex;
    padding: 0 50px;

    .button {
      margin-left: 50px;
    }
  }
}

.todo-list {

  &__header {
    padding: 20px 0;
    display: flex;
    justify-content: space-between;
  }

  &__item {
    display: flex;
    justify-content: space-between;
    padding: 10px 0 20px 0;
    border-top: 1px solid #BDBDBD;

    &--completed {
      p {
        color: #BDBDBD;
        text-decoration: line-through;
      }
    }
  }
}
</style>
