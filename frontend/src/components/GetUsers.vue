<template>
  <div>
    <ul v-if="posts && posts.length">
      <li v-for="(post, index) of posts" :key="index">
        <p><strong>{{post.email}}</strong></p>
        <p>{{post.password}}</p>
      </li>
    </ul>

    <ul v-if="errors && errors.length">
      <li v-for="(error, index) of errors" :key="index">
        {{error.message}}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      posts: [],
      errors: []
    }
  },

  // Fetches posts when the component is created.
  async created() {
    try {
      const response = await axios.get("http://localhost:8080/user")
      this.posts = response.data
    } catch (e) {
      this.errors.push(e)
    }
  }
}
</script>
