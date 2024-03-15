<script lang="ts" setup>
const { assets } = await GqlAssets({ per_page: 30 });
</script>
<template>
  <h1 class="text-4xl mb-2 font-bold">Hygraph stock library starter</h1>
  <p class="mb-8">All images here come from pexels.com and are royalty free.</p>
  <div class="grid grid-cols-4 gap-4">
    <card :asset="asset" v-for="asset in assets" :key="asset.id" />
  </div>
</template>
