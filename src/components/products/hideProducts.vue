<script setup>
  import Toggle from '../Toggle.vue';
  import Pagination from '../Pagination.vue';

  const products = [
    {
      code: 'AF005',
      title: 'AFD Coolmax Bandana AFD',
      active: true,
    },
    {
      code: 'AF006',
      title: "AFD Short Sleeve Coolmax Chef's Jacket AFD",
      active: false,
    },
    {
      code: 'AF009',
      title: "AFD Short Sleeve Chef's Tunic AFD",
      active: true,
    },
  ];
</script>

<template>
  <div class="mt-10">
    <p class="text-sm text-gray-700 mb-6">
      If you don’t want to show a particular product, then you can hide these
      below. Hiding a product type here will prevent any products of that type
      being shown anywhere on your website. Any changes you make will take
      effect instantly.
    </p>
    <div class="flex space-x-4 items-center mb-4 text-gray-700">
      <input
        type="text"
        class="input"
        name="search"
        placeholder="Search for a product by code or name..."
        id="search"
      />
      <label for="hiddenOnly" class="label whitespace-nowrap">
        <input type="checkbox" name="hiddenOnly" id="hiddenOnly" class="p-1" />
        Only show hidden
      </label>
    </div>

    <div v-for="product in products" v-bind:key="product.code">
      <Toggle :model="product.active">{{ product.title }}</toggle>
    </div>
    <pagination />
  </div>
</template>
