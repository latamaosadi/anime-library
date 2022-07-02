<script setup>
import { ref } from 'vue';
import axios from 'axios';
import AnimeList from './components/AnimeList.vue';

const items = ref([]);
const keyword = ref('');
const loading = ref(false)

async function searchAnime() {
  items.value = [];
  loading.value = true;
  const { data } = await axios.get('https://api.jikan.moe/v4/anime', {
    params: {
      q: keyword.value
    }
  });
  items.value = data.data;
  loading.value = false;
}

</script>

<template>
  <div class="max-w-xl mx-auto p-10 text-center">
    <form @submit.prevent="searchAnime" class="flex space-x-2 items-center justify-center">
      <input type="text" class="form-input" v-model="keyword" placeholder="Search for anime..." />
      <button type="submit" class="px-4 py-2 bg-blue-600 text-white">Search</button>
    </form>
    <div class="mt-20">
      <div v-if="loading" class="text-center text-xl">
        Loading...
      </div>
      <AnimeList v-else :items="items" />
    </div>
  </div>
</template>
