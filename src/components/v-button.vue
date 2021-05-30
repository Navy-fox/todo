<template>
<div class="button" :style="'background-color:' + color">
  <img :src="`/img/${icon}.svg`" alt="">
</div>
</template>

<script>
export default {
  name: "v-button",
  props: {
    color:{
      type:String,
      required:true
    },
    icon:{
      type:String,
      default:"plus-fill"
    }
  }
}
</script>

<style lang="scss">
.button {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 25px;
  height: 25px;
  border-radius: 5px;
  background-color: navy;
}
</style>