<template>
  <div class="home">
    <h1>Home</h1>
    <div class="error" v-if="error">{{ error }}</div>
    <div v-if="posts.length">
      <PostList  v-if="showPost" :posts="posts"/>
    </div>
    <div v-else>Loading...</div>
    <button @click="showPost=!showPost">Toggle Posts</button>
  </div>
</template>

<script>
import { ref } from '@vue/reactivity'
import PostList from '@/components/PostList.vue'
import getPosts from '../composables/getPosts.js'

export default {
  name: 'Home',
  components: {
    PostList
  },
  setup() {
    const showPost = ref(true)

    const { posts, error, load } = getPosts()
    load()

    return { posts, showPost, error }
  }
}
</script>

<style>
button {
  border: 0;
  padding: 10px;
  background-color: crimson;
  color: white;
  border-radius: 5px;
}
</style>
