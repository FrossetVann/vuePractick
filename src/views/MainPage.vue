<script setup>
import axios from 'axios';
import CardList from '../components/CardList.vue'
import { ref, computed, reactive, onMounted, warn, watch } from "vue";
  let search = ref('')
  const wines = ref([])



const FetchWines = async () => {
  try{
    const {data} = await axios.get(
      `https://e6c7f09dff4a57b0.mokky.dev/wines?title='*${search.value}*`
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

const onchangeSearch = (event) => {
    search.value = event.target.value
    console.log(search.value)
  }

watch(FetchWines)

</script>

<template>
      <h2 class="text-2xl">Товары</h2>
    <div class="flex gap-4 items-center">
      <input  @input="onchangeSearch" type="text" class="p-2 border-2 border-red-800 rounded-lg focus:outline-none " placeholder="Искать...">
      <span class="text-slate-400">Сахар:</span>
      <select class="p-2 border-2 border-red-800 rounded-lg focus:outline-none">
        <option value="сладкое">сладкое</option>
        <option value="полусладкое">полусладкое</option>
        <option value="полусухое">полусухое</option>
        <option value="сухое">сухое</option>
      </select>
      <span class="text-slate-400">Цвет:</span>
      <select class="p-2 border-2 border-red-800 rounded-lg focus:outline-none">
        <option value="красное">красное</option>
        <option value="белое">белое</option>
      </select>
    </div>
    
    <CardList :wines="wines"/>
</template>