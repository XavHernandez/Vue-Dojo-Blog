<template>
  <div class="home">
    <h1>Home</h1>
  </div>
</template>

<script>
import { ref } from '@vue/reactivity'

export default {
  name: 'Home',
  components: {},
  setup() {
    const posts = ref([
      { title: 'Welcome to the Blog', body: 'Lorem Ipsum', id: 1 },
      { title: 'Top 5 CSS Tips', body: 'Lorem Ipsum', id: 2 }
    ])

    return { posts }
  }
}
</script>
