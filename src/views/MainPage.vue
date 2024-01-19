<script setup>
import WineCard from '../components/WineCardComp.vue';

import { ref, computed, reactive } from "vue";
  let search = ref("")

  const wines = reactive([
  {id: 1, title: "Кьянти Ризерва", country: "Italy", volume: 1, price: 799},
  {id: 2, title: "Пьетраме Пино", country: "Italy", volume: 1, price: 799},
  {id: 3, title: "Стеммари Москато", country: "Italy", volume: 1, price: 799},
  {id: 4, title: "Трамонтана Апулия", country: "Italy", volume: 1, price: 799},
  {id: 5, title: "Портвейн", country: "Italy", volume: 1, price: 799},
])
 const wines2 = ["Кьянти Ризерва","Пьетраме Пино","Пьетраме Пино","Стеммари Москато"]

const searchedProducts = computed(() => {
      return wines.filter((wine) => {
        return (
          wine.title
            .toLowerCase()
            .indexOf(search.value.toLowerCase()) != -1
        );
      });
});

</script>

<template>
      <h2 class="text-2xl">Товары {{ search }}</h2>

    <input  v-model="search" type="text" class="p-2 border-2 border-red-800 rounded-lg focus:outline-none " placeholder="Искать...">
    
    <section class="section">
      <WineCard
      :title="wine.title"
      :country="wine.country"
      :type="wine.type" 
      :volume="wine.volume" 
      :price="wine.price" 
      v-for="wine in searchedProducts" :key="wine.id">
      </WineCard>
    </section>
    <div class="item error" v-if="search&&!searchedProducts.length">
      <p>Ничего не нашлось!</p>
    </div>
    <h2 class="text-2xl">Закладки</h2>
    <section class="section">

    </section>
</template>