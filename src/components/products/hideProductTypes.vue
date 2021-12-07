<script setup>
  import Toggle from '../Toggle.vue';

  const types = [
    {
      title: 'Accessory',
      active: true,
    },
    {
      title: 'All in One',
      active: true,
    },
    {
      title: 'Apron',
      active: true,
    },
  ];
</script>

<template>
  <div class="mt-10">
    <p class="text-sm text-gray-700 mb-6">
      If you don’t want to show a particular type of product, then you can hide
      these below. Hiding a product type here will prevent any products of that
      type being shown anywhere on your website. Any changes you make will take
      effect instantly.
    </p>
    <div class="flex space-x-4 items-center mb-4 text-gray-700">
      <input
        type="text"
        class="input"
        name="search"
        placeholder="Search for a product type..."
        id="search"
      />
      <label for="hiddenOnly" class="label whitespace-nowrap mb-0">
        <input type="checkbox" name="hiddenOnly" id="hiddenOnly" class="p-1" />
        Only show hidden
      </label>
    </div>

    <div v-for="type in types" v-bind:key="type.title">
      <Toggle :model="type.active">{{ type.title }}</Toggle>
    </div>
  </div>
</template>
