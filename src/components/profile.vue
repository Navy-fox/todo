<template>
  <div class="profile">
    <router-link :to="`/todo/${item.id}`" class="profile__card card" v-for="(item,key) in users" :key="key">
      <p class="card__item">Name: {{ item.name }}</p>
      <p class="card__item">e-mail: {{ item.email }}</p>
      <p class="card__item">Web-site: {{ item.website }}</p>
    </router-link>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "profile",
  data: () => ({
    users: []
  }),
  async created() {
    const res = await axios.get('https://jsonplaceholder.typicode.com/users')
    this.users = res.data
  }
}
</script>

<style lang="scss">
.profile{
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-column-gap: 20px;
  grid-row-gap: 20px;
}

.card {
  padding: 5px;
  border: 1px solid #BDBDBD;
  border-radius: 5px;
  &__item {
    margin: 10px;
  }
}
</style>