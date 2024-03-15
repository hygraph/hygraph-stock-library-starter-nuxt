<script setup lang="ts">
defineProps(["asset"]);
</script>

<template>
  <figure class="hover:shadow-xl">
    <nuxt-link :to="`/asset/${asset.id}`" class="block relative">
      <img
        :src="`${asset.grid}/${asset.fileName}`"
        :alt="asset.alt"
        loading="lazy"
        width="300"
        height="300"
        class="w-full h-auto block hover:opacity-80 transition ease duration-500"
      />
      <figcaption
        class="text-gray-100 p-2 absolute bottom-0 left-0 w-full h-auto bg-gray-800/60"
      >
        <p class="line-clamp-1 text-sm">{{ asset.alt }}</p>
        <p class="text-xs text-gray-300">
          {{ asset.width }}x{{ asset.height }} &mdash;
          {{ asset.createdBy.name }}
        </p>
      </figcaption>
    </nuxt-link>
  </figure>
</template>
