<script setup>
import axios from 'axios';
import CardList from '../components/CardList.vue'
import { ref, computed, reactive, onMounted } from "vue";
  // let search = ref("")
  const wines = ref([])

// const searchedProducts = computed(() => {
//       return wines.filter((wine) => {
//         return (
//           wine.title
//             .toLowerCase()
//             .indexOf(search.value.toLowerCase()) != -1
//         );
//       });
// });

const FetchWines = async () => {
  try{
    const {data} = await axios.get(
      'https://e6c7f09dff4a57b0.mokky.dev/wines'
    )

    wines.value = data
    console.log(data)
  } catch (err) {
    console.log(err)
  }
}

onMounted(async () => {
  await FetchWines()
})

</script>

<template>
      <h2 class="text-2xl">Товары</h2>

    <input  v-model="search" type="text" class="p-2 border-2 border-red-800 rounded-lg focus:outline-none " placeholder="Искать...">
    
    <CardList :wines="wines"/>

    <!-- <div class="item error" v-if="search&&!searchedProducts.length">
      <p>Ничего не нашлось!</p>
    </div> -->
    <h2 class="text-2xl">Закладки</h2>
    <section class="section">

    </section>
</template>