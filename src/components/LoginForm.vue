<template>
  <form>
    <div>
      <label for="username">Username</label>
      <input type="text" name="username" v-model="username" />
    </div>
    <div>
      <label for="password">Password</label>
      <input bg="green-100" type="password" name="password" v-model="password" />
    </div>
    <div>
      <button bg="blue-400 hover:green-500" text="sm white" type="submit" @click.prevent="handleSubmit">Log In</button>
    </div>
  </form>
</template>

<script lang="ts">

import { defineComponent } from 'vue'

export default defineComponent({
  setup() {
    const username = ref('')
    const password = ref('')
    const handleSubmit = () => {
      // Do something with username and password
    }

    return {
      username,
      password,
      handleSubmit
    }
  }
})
</script>
