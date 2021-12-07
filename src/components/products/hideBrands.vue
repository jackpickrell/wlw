<script setup>
  import Toggle from '../Toggle.vue';

  const brands = [
    {
      title: 'AFD',
      active: true,
    },
    {
      title: 'Anthem',
      active: true,
    },
    {
      title: 'BagBase',
      active: true,
    },
    {
      title: 'Beechfield',
      active: true,
    },
  ];
</script>

<template>
  <div class="mt-10">
    <p class="text-sm text-gray-700 mb-6">
      If you don’t want to show products for one or more brands, then you can
      hide these brands below. Hiding a brand will prevent any products for that
      brand being shown anywhere on your website. Any changes you make will take
      effect instantly.
    </p>
    <div class="flex space-x-4 items-center mb-4 text-gray-700">
      <input
        type="text"
        class="input"
        name="search"
        placeholder="Search for a brand..."
        id="search"
      />
      <label for="hiddenOnly" class="label whitespace-nowrap">
        <input type="checkbox" name="hiddenOnly" id="hiddenOnly" />
        Only show hidden
      </label>
    </div>

    <div v-for="brand in brands" v-bind:key="brand.title">
      <Toggle model="brand.active">{{ brand.title }}</Toggle>
    </div>
  </div>
</template>
