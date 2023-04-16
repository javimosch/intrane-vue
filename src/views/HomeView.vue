<template>
  <div class="grid h-screen place-items-center">
    <div class="space-x-2">
      <h3 text="center">create unocss button using preset-attributify </h3>
      <button
        bg="blue-400 hover:blue-500"
        text="sm white"
        font="mono light"
        p="y-2 x-4"
        border="2 rounded blue-200"
      >
        Button
      </button>
      <button
        bg="red-400 hover:red-800"
        text="xl white"
        font="mono bold"
        p="y-2 x-20"
        border="2 rounded red-800"
      >
        Remove
        <div class="i-tabler:brand-vue text-3xl" />
      </button>
      <button
        bg="green-400 hover:green-500"
        text="sm white"
        font="mono light"
        p="y-2 x-4"
        border="2 rounded green-200"
      >
        Button
      </button>
    </div>
    <LoginForm/>
  </div>
</template>
<script setup lang="ts">

</script>