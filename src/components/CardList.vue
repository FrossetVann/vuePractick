<script setup>
import WineCard from '../components/WineCard.vue';

defineProps({
  wines: Array,
})
</script>

<template>
  <section class="section" v-if="wines.length!=0">
    <WineCard 
    :title="wine.title" 
    :color="wine.color" 
    :sugar="wine.sugar" 
    :country="wine.country"
    :alcohol="wine.alcohol"
    :price="wine.price"
    :image="wine.image"
    v-for="wine in wines" :key="wine.id">
    </WineCard>
  </section>
  <div class="item error" v-else>
      <p class="text-xl">Ничего не нашлось!</p>
    </div>
</template>