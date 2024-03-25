<script lang="ts" setup>
import prettyBytes from "pretty-bytes";

const route = useRoute();
const id = route.params.id as string;
const { asset } = await GqlAsset({ id });

const size = computed(() => {
  return prettyBytes(asset?.size || 0);
});

const dateString = computed(() => {
  return new Date(asset?.publishedAt).toLocaleDateString("en-US", {
    dateStyle: "full",
  });
});
</script>
<template>
  <p class="mb-2">
    <nuxt-link to="/" class="underline text-xs uppercase"
      >Back to index</nuxt-link
    >
  </p>
  <div class="mb-4 flex space-x-2 items-center">
    <img
      v-if="asset?.createdBy?.picture"
      :src="asset?.createdBy?.picture"
      class="w-6 rounded-full"
      loading="lazy"
      width="50"
      height="50"
    />
    <p class="font-bold">{{ asset?.createdBy?.name }}</p>
  </div>
  <h1 class="text-4xl mb-1 font-bold">{{ asset?.alt }}</h1>
  <p class="text-sm text-gray-500 mb-2">
    {{ asset?.width }}x{{ asset?.height }}, {{ asset?.mimeType }}, {{ size
    }}<br />
    {{ dateString }}
  </p>
  <a
    :href="asset?.original"
    target="_blank"
    class="inline-block mb-6 text-sm bg-slate-800 text-slate-100 py-2 px-4 rounded-md uppercase hover:bg-slate-600"
    >Download original</a
  >
  <figure class="relative">
    <img
      v-if="asset"
      :src="asset.hero"
      :alt="asset?.alt || ''"
      :width="asset?.width || 160"
      :height="asset?.height || 90"
      loading="eager"
      class="block w-full h-auto rounded-md"
    />
    <figcaption
      class="text-gray-100 p-2 absolute bottom-0 left-0 w-full h-auto bg-gray-800/60"
    >
      {{ asset?.fileName }}
    </figcaption>
  </figure>
</template>
