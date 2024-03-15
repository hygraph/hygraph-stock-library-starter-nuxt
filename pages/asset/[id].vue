<script lang="ts" setup>
import prettyBytes from "pretty-bytes";

const route = useRoute();
const id = route.params.id;
const { asset } = await GqlAsset({ id });

const size = computed(() => {
  return prettyBytes(asset.size);
});

const dateString = computed(() => {
  return new Date(asset.publishedAt).toLocaleDateString("en-US", {
    dateStyle: "full",
  });
});
</script>
<template>
  <p class="mb-2">
    <nuxt-link to="/" class="underline text-xs">&lt; Back to index</nuxt-link>
  </p>
  <div class="mb-4 flex space-x-2 items-center">
    <img
      :src="asset.createdBy.picture"
      class="w-6 rounded-full"
      loading="lazy"
      width="50"
      height="50"
    />
    <p class="font-bold">{{ asset.createdBy.name }}</p>
  </div>
  <h1 class="text-4xl mb-1 font-bold">{{ asset.alt }}</h1>
  <p class="text-sm text-gray-500 mb-6">
    {{ asset.width }}x{{ asset.height }}, {{ asset.mimeType }}, {{ size }}<br />
    {{ dateString }}
  </p>
  <figure class="relative">
    <img
      :src="asset.hero"
      :alt="asset.alt"
      :width="asset.width"
      :height="asset.height"
      loading="eager"
      class="block w-full h-auto rounded-md"
    />
    <figcaption
      class="text-gray-100 p-2 absolute bottom-0 left-0 w-full h-auto bg-gray-800/60"
    >
      {{ asset.fileName }}
    </figcaption>
  </figure>
</template>
