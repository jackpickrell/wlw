<script setup>
import { ref } from 'vue';
import Toggle from '../Toggle.vue';

const showStock = ref(true);
const showPricing = ref(true);
const showVat = ref(true);
const showDialog = ref(false);
</script>

<template>
  <div class="mt-10">
    <p class="text-sm text-gray-700">
      You can change the way products are presented below.
    </p>
    <form class="mt-5">
      <Toggle :model="showStock">
        <p class="mb-2">Show Stock</p>
        <p class="text-xs font-normal">
          Display available stock for products on your website.
        </p>
      </Toggle>
      <Toggle :model="showPricing">
        <p class="mb-2">Show Pricing</p>
        <p class="text-xs font-normal">
          Display end user pricing on your website using a
          <button
            @click="showDialog = true"
            type="button"
            class="text-primary-500"
          >
            sliding percentage markup</button
          >.
        </p>
      </Toggle>
      <Toggle :model="showVat">
        <p class="mb-2">Show VAT</p>
        <p class="text-xs font-normal">
          Display end user prices inclusive of VAT.
        </p>
      </Toggle>
      <div class="py-4 sm:py-5">
        <label
          for="description"
          class="label"
        >
          Additional product note
        </label>
        <div class="mt-2">
          <textarea
            id="description"
            name="description"
            rows="4"
            class="input"
          />
        </div>
        <p class="text-xs mt-2.5 text-gray-700">
          Add any text here that you would like to appear on every product page.
        </p>
      </div>
    </form>
    <div v-if="showDialog">
      <div
        @click="showDialog = false"
        class="fixed inset-0 bg-black bg-opacity-50"
      ></div>
      <div class="fixed top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2">
        <div class="bg-white p-8 rounded-lg">
          <table
            class="min-w-full divide-y divide-gray-200 text-gray-500 text-xs"
          >
            <thead class="bg-gray-50">
              <tr>
                <th
                  scope="col"
                  class="px-4 py-3 font-medium uppercase tracking-wider"
                >
                  PenCarrie Single Price
                </th>
                <th
                  scope="col"
                  class="px-4 py-3 font-medium uppercase tracking-wider"
                >
                  Single Price Plus
                </th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td class="px-4 py-2 text-sm whitespace-nowrap">
                  £0.00 - £1.49
                </td>
                <td class="px-4 py-2 text-sm whitespace-nowrap">100%</td>
              </tr>
              <tr>
                <td class="px-4 py-2 text-sm whitespace-nowrap">
                  £1.50 - £3.00
                </td>
                <td class="px-4 py-2 text-sm whitespace-nowrap">75%</td>
              </tr>
              <tr>
                <td class="px-4 py-2 text-sm whitespace-nowrap">
                  £3.01 - £7.00
                </td>
                <td class="px-4 py-2 text-sm whitespace-nowrap">65%</td>
              </tr>
              <tr>
                <td class="px-4 py-2 text-sm whitespace-nowrap">
                  £7.01 - £12.99
                </td>
                <td class="px-4 py-2 text-sm whitespace-nowrap">60%</td>
              </tr>
              <tr>
                <td class="px-4 py-2 text-sm whitespace-nowrap">£13.00+</td>
                <td class="px-4 py-2 text-sm whitespace-nowrap">55%</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>
