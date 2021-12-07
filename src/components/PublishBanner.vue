<template>
  <div v-if="published" class="bg-green-500 bg-opacity-20 py-4 md:ml-64 px-8">
    <div class="flex justify-between items-center space-x-5">
      <div class="flex">
        <CheckIcon class="w-6 h-6 inline-block text-green-500 flex-shrink-0 mr-2 mt-1" />
        <p class="text-green-700">
          Your website is currently <strong>published</strong>, which means no
          one but you can see it.
        </p>
      </div>
      <div
        class="flex flex-col md:flex-row space-y-1 md:space-y-0 md:space-x-2"
      >
        <button
          class="
            border-2 border-primary-500
            text-primary-700
            hover:bg-primary-500 hover:text-white
            px-6
            py-2
            rounded-lg
          "
        >
          View
        </button>
        <button @click="published = false" class="btn bg-red-500 text-white">Unpublish</button>
      </div>
    </div>
  </div>

  <div v-else class="bg-yellow-200 bg-opacity-20 py-4 md:ml-64 px-8">
    <div class="flex justify-between items-center space-x-5">
      <div class="flex">
        <ExclamationIcon class="w-6 h-6 inline-block text-yellow-500 flex-shrink-0 mr-2 mt-1" />
        <p class="text-yellow-700">
          Your website is currently <strong>unpublished</strong>, which means no
          one but you can see it.
        </p>
      </div>
      <div
        class="flex flex-col md:flex-row space-y-1 md:space-y-0 md:space-x-2"
      >
        <button
          class="
            border-2 border-primary-500
            text-primary-700
            hover:bg-primary-500 hover:text-white
            px-6
            py-2
            rounded-lg
          "
        >
          Preview
        </button>
        <button @click="published = true" class="btn-primary">Publish</button>
      </div>
    </div>
  </div>
</template>

<script>
import { ExclamationIcon, CheckIcon } from '@heroicons/vue/outline';

export default {
  components: { ExclamationIcon, CheckIcon },
  props: ['published'],
};
</script>
