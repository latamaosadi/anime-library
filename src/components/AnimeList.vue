<script setup>
import AnimeListItem from './AnimeListItem.vue';
const props = defineProps({
  items: { default: () => [], type: Array }
});
</script>

<template>
  <div class="grid gap-12">
    <AnimeListItem v-for="(item, index) in items" :item="item" :key="index" />
  </div>
</template>

<style lang="scss" scoped>
</style>