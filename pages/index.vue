<script lang="ts" setup>
const { assets } = await GqlAssets({ per_page: 30 });
</script>
<template>
  <h1 class="text-4xl mb-2 font-bold">Hygraph stock library starter</h1>
  <p class="mb-8">All images here come from pexels.com and are royalty free.</p>
  <p class="flex space-x-2 mb-8">
    <a
      href="https://app.hygraph.com/clone/6b3636b3c7914fe5904fd41e364bc1cf?name=Asset%20Management%20Workshop"
      target="_blank"
      class="block text-sm bg-slate-800 text-slate-100 py-2 px-4 rounded-md uppercase hover:bg-slate-600"
      >Clone the Hygraph project</a
    >
    <a
      href="https://github.com/hygraph/hygraph-stock-library-starter-next"
      target="_blank"
      class="block text-sm bg-slate-800 text-slate-100 py-2 px-4 rounded-md uppercase hover:bg-slate-600"
      >Get the code for Next.js</a
    >
    <a
      href="https://github.com/hygraph/hygraph-stock-library-starter-nuxt"
      target="_blank"
      class="block text-sm bg-slate-800 text-slate-100 py-2 px-4 rounded-md uppercase hover:bg-slate-600"
      >Get the code for NuxtJS</a
    >
  </p>
  <div class="grid grid-cols-4 gap-4">
    <card :asset="asset" v-for="asset in assets" :key="asset.id" />
  </div>
</template>
