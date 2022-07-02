<template>
  <div class="PageDisplay">
    <div v-for='(gettersUser, index) in users' :key='index'>
      <b>{{gettersUser.email}}</b><br/>
      {{gettersUser.password}}<br/>
      <button @click="removeUser(gettersUser.id)">Delete</button><br/><br/>
    </div>
    <div>
      <button @click="addRandomUser()">New random email</button>
    </div>
  </div>
</template>

<script>
import { onMounted, defineComponent } from 'vue';
import { storeToRefs } from "pinia";
import { useUserStore } from "../stores/users";

export default defineComponent({
  setup() {
    const store = useUserStore();
    const { users } = storeToRefs(store)
    const { fetchUsers, addUser, deleteUser } = store
    onMounted(() => {
      store.fetchUsers();
    })
    return {
      users, fetchUsers, addUser, deleteUser
    }
  },
  methods: {
    addRandomUser() {
      const email = Math.random().toString(16).substring(2,8) + "@website.com"
      const password = Math.random().toString(16)
      console.log(email + " " + password)
      let response = this.addUser(email, password)
      this.fetchUsers();
      return response
    },
    removeUser(id) {
      return this.deleteUser(id)
    }
  }
})
</script>