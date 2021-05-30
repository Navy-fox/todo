<template>
  <div class="home">
    <profile></profile>
  </div>
</template>

<script>
// @ is an alias to /src

import Profile from "../components/profile";
export default {
  name: 'Home',
  components: {
    Profile
  }
}
</script>
