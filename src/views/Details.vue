<template lang="">
  <div v-if="error">
    {{error}}
  </div>
  <div v-if="post" class="post">
  <h3>{{post.title}}</h3>
  <p class="pre">{{post.body}}</p>
  </div>
</template>
<script>
import getPostById from '../composables/getPostById'

export default {
  props: ['id'],
  setup(props) {
    const { post, error, load } = getPostById(props.id)

    load()

    return {
      post,
      error
    }
}
}
</script>
<style >
.post {
  max-width: 1200px;
  margin: 0 auto;
}

.post p {
  color: #333;
  line-height: 1.5em;
  margin-top: 40px;
}

.pre {
  white-space: pre-wrap;
  word-wrap: break-word;
}
</style>