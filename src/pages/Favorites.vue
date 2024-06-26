<script setup>
import { onMounted, ref } from 'vue'
import axios from 'axios'

const favorites = ref([])


onMounted(async () => {
  try {
    const { data } = await axios('https://ddd25c3e3f7d47f3.mokky.dev/favorites?_relations=items')
    favorites.value = data

  } catch (err) {
    console.log(err)
  }
})
</script>

<template>
  <div v-for="favorite in favorites" class="grid grid-cols-3 gap-7" v-auto-animate>
    <div class="relative bg-white border border-slate-100 rounded-3xl p-8 m-2 cursor-pointer hover:-translate-y-2 hover: shadow-xl transition">
      <img :src="favorite.item.imageUrl" alt="Sneaker" />
      <p class="mt-3">{{ favorite.item.title }}</p>
      <div class="flex justify-between mt-5">
        <div class="flex flex-col">
          <span class="text-slate-400">Цена: </span>
          <b>{{ favorite.item.price }} руб.</b>
        </div>
      </div>
    </div>
  </div>
  <div v-if="favorites.length === 0">
    <h1 class="text-3xl font-bold mb-8">У вас нету избранных...</h1>
  </div>
</template>