<template>
  <div>
    <input type="text" v-model="postEmail" />
    <input type="text" v-model="postPassword" />
    <button @click="postPost">submit</button>
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
      postEmail: '',
      postPassword: '',
      user: {},
      errors: []
    }
  },

  methods: {
    // Pushes posts to the server when called.
    async postPost() {
      try {
        const response = await axios.post("http://localhost:8080/user", {
          email: this.postEmail,
          password: this.postPassword
        })
        this.user = response;
      } catch (e) {
        this.errors.push(e)
      }
    }
  }
}
</script>