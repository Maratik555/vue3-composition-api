<script setup>
defineProps({
  totalPrice: Number
});
const emit = defineEmits(['openDrawer'])

</script>

<template>
    <header class="flex justify-between border-b border-slate-200 px-10 py-8">
    <router-link to="/"><div class="flex items-center gap-4">
      <img class="w-12" src="/logo.png" alt="logo">
      <div>
        <h2 class="text-xl font-bold uppercase">Vue Shop</h2>
        <p class="text-slate-400">Магазин лучших кроссовок</p>
      </div>
    </div></router-link>


        <ul class="flex items-center gap-10">
            <li @click="() => emit('openDrawer')"
                class="flex items-center gap-4 cursor-pointer text-gray-600 hover:text-black">
                <img src="/cart.svg" alt="Cart">
                <b>{{ totalPrice }} ₽</b>
            </li>
          <router-link to="/favorites">
            <li class="flex items-center gap-4 cursor-pointer text-gray-600 hover:text-black">
              <img src="/heart.svg" alt="bookmarks">
              <span>Избранное</span>
            </li>
          </router-link>
          <router-link to="/profile">
            <li class="flex items-center gap-4 cursor-pointer text-gray-600 hover:text-black">
              <img src="/profile.svg" alt="Profile">
              <span>Профиль</span>
            </li>
          </router-link>

        </ul>

        <!--      <nav>-->
        <!--        <RouterLink to="/">Home</RouterLink>-->
        <!--        <RouterLink to="/about">About</RouterLink>-->
        <!--      </nav>-->

    </header>
</template>
