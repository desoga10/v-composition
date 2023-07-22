<template >
  <div>
    <h2>Home</h2>
    <span v-if="error">{{ error }}</span>
    <div v-if="posts.length">
      <PostList :posts="posts" />
    </div>
    <div v-else>Loading</div>
  </div>
</template>
<script>
import PostList from '../components/PostList.vue'
import getPosts from '../composables/getPosts'

export default {
  name: 'Home',
  components: { PostList },
  setup() {
    const { posts, error, load} = getPosts()
    load()
    return { posts, error }
  },
}
</script>
<style ></style>