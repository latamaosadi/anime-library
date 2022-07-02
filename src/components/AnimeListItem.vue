<script setup>
const props = defineProps({
  item: { default: {}, type: Object }
});
</script>

<template>
  <div class="relative flex">
    <div class="h-40 w-40 relative">
      <img :src="props.item.images.jpg.image_url" alt="" class="absolute inset-0 h-full w-full object-cover">
    </div>
    <div class="p-4 flex-1 text-left">
      <h4 class="font-medium text-lg text-neutral-600">{{ props.item.title }}</h4>
      <ul class="flex flex-wrap mt-3">
        <li v-for="(genre, index) in props.item.genres" :key="index" class="p-1">
          <span class="text-xs text-white bg-blue-600 px-2 py-1 rounded">{{ genre.name }}</span>
        </li>
      </ul>
    </div>
  </div>
</template>

<style lang="scss" scoped>
</style>