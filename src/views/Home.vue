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
import PostList from '@/components/PostList.vue'
import { ref } from '@vue/reactivity'

export default {
  name: 'Home',
  components: {
    PostList
  },
  setup() {
    const posts = ref([])
    const error = ref(null)

    const showPost = ref(true)

    const load = async () => {
      try { 
        let data = await fetch('http://localhost:3000/posts')
        if (!data.ok) {
          throw Error ('No data available')
        }
        posts.value = await data.json()
      } 
      catch (err) {
        error.value = err.message
      }
    }

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
