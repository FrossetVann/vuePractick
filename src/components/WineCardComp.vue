<script setup>
  defineProps({
    title: String,
    country: String,
    type: String,
    volume: Number,
    price: Number,
  })

</script>

<template>
  <div class="w-48 h-{86rem}  rounded-md bg-slate-400 overflow-hidden ">
    <div class="w-full h-48 bg-white flex justify-center items-center">
    <img src="/wine.jpg" alt="wine" class="h-full bg-cyan-300  ">
    </div>
    
    <h4>{{ title }}</h4>
    <h4>{{ country }}</h4>
    <h4>{{ type }}</h4>
    <h4>{{ volume }}</h4>
    <h4>{{ price }}</h4>
  </div>
</template>

