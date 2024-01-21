<script setup>
  defineProps({
    title: String,
    color: String,
    sugar: String,
    country: String,
    alcohol: Number,
    price: String,
    image: String,
  })

</script>

<template>
  <div class="w-48 h-{86rem}  rounded-lg  overflow-hidden border-2 border-slate-100 hover:-translate-y-2 hover:shadow-xl transition">
    <div class="w-full h-48 bg-white flex justify-center items-center">
    <img :src="image" alt="wine" class="h-full scale-90">
    </div>
    <div class="border-t border-slate-100 p-2 flex flex-col flex-1">
      <h4 class="text-lg ">{{ title }}</h4>
      <span class="text-slate-400">{{ color }}, </span>
      <span class="text-slate-400">{{ sugar }}, </span>
      <span class="text-slate-400">{{ alcohol }}% </span>
      <span class="text-slate-400">{{ country }}</span>
      <b class="relative bottom-0">{{ price }}</b>
    </div>
  </div>
</template>

