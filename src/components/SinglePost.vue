<template>
  <li>
    <div
        class="inline-block text-red-500"
        :class="{'fav' : post.fav}">
      {{ post.title }}
    </div> |
    <button @click="handleClick(post)" class="px-1 border border-blue-400 rounded-md bg-blue-100 mb-2">Delete Post</button> |
    <button @click="$emit('fav', post)" class="px-1 border border-green-400 rounded-md bg-green-100 mb-2">Fav Post</button>
  </li>
</template>
<!--        :class="[post.fav?'fav':'']">-->
<script>
export default {
  name: "SinglePost",
  props: ['post'],
  // props: {
  //   post:{
  //     type: Object,
  //     required: true
  //   }
  // }
  methods: {
    handleClick(post){
      // console.log(post)
      this.$emit('delete', post)
    }
  }
}
</script>

<style scoped>
  .fav{
    color: green;
  }
</style>