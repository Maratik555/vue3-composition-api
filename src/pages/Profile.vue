<script setup>

import { onMounted, ref, watch } from 'vue'

const name = ref('')
const user = ref([])

const profile = e => {
  e.preventDefault()
  user.value.push(name.value)
  name.value = ''
}

watch(user, () => {
  localStorage.setItem('user', JSON.stringify(user.value))
}, { deep: true })

onMounted(() => {
  user.value = JSON.parse(localStorage.getItem('user')) || []
})
</script>

<template>
  <div v-if="!user.length">
    <form autocomplete="on">
      <h2 class="text-3xl font-bold mb-8">Profile</h2>
      <input class="border border-slate-300 p-2 w-60" type="text" placeholder="Enter your name" v-model="name">
      <br/><br>
      <button @click="profile" :disabled="!name" class="border border-blue-700 p-2 w-60 h-13 rounded-3xl text-center cursor-pointer hover:bg-sky-700">Create user</button>
      <br><br>
    </form>
  </div>
  <div v-if="user.length" class="text-2xl mb-5">
    <div class="border border-green-500 p-2 w-60 h-13 rounded-3xl text-center hover:-translate-y-2 hover: shadow-xl transition"> Hello, {{user.join(' ')}} !</div>
    <button @click="user = []" class="border border-blue-700 p-2 mt-5 w-60 h-13 rounded-3xl text-center cursor-pointer hover:bg-sky-700">Logout</button>
  </div>
</template>