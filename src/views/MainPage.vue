<script setup>
import axios from 'axios';
import CardList from '../components/CardList.vue'
import { ref, computed, reactive, onMounted, warn, watch } from "vue";

const wines = ref([])

const filters = reactive({
  search: '',
  sugar: '',
  color: '',

})

const onChangeSelectSugar = (event) => {
  filters.sugar = event.target.value
  console.log(filters.sugar)
}
const onChangeSelectColor = (event) => {
  filters.color = event.target.value
  console.log(filters.color)
}
const onChangeSearch = (event) => {
  filters.search = event.target.value
  console.log(filters.search)
}

const FetchWines = async () => {
  try {
    const params = {
      // title: '',
      // sugar: filters.sugar,
      // color: filters.color
    }
    if (filters.search) {
      params.title = `*${filters.search}*`
    }
    if (filters.color) {
      params.color = `${filters.color}`
    }
    if (filters.sugar) {
      params.sugar = `${filters.sugar}`
    }
    const { data } = await axios.get(
      `https://e6c7f09dff4a57b0.mokky.dev/wines`,
      {
        params
      }
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



watch(
  FetchWines,
)

</script>

<template>
  <h2 class="text-2xl">Товары</h2>
  <div class="flex gap-4 items-center">
    <input @input="onChangeSearch" type="text" class="p-2 border-2 border-red-800 rounded-lg focus:outline-none "
      placeholder="Искать...">
    <span class="text-slate-400">Сахар:</span>
    <select @change="onChangeSelectSugar" class="p-2 border-2 border-red-800 rounded-lg focus:outline-none">
      <option value="">все</option>
      <option value="сладкое">сладкое</option>
      <option value="полусладкое">полусладкое</option>
      <option value="полусухое">полусухое</option>
      <option value="сухое">сухое</option>
    </select>
    <span class="text-slate-400">Цвет:</span>
    <select @change="onChangeSelectColor" class="p-2 border-2 border-red-800 rounded-lg focus:outline-none">
      <option value="">все</option>
      <option value="красное">красное</option>
      <option value="белое">белое</option>
    </select>
  </div>

  <CardList :wines="wines" />
</template>