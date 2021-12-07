<template>
  <div
    class="
      bg-yellow-200
      border-l-4 border-yellow-600
      text-yellow-600
      bg-opacity-20
      p-4
    "
  >
    <div class="flex items-center">
      <component :is="ExclamationIcon" class="w-6 h-6 flex-shrink-0 mr-2" />
      <p class="text-sm">
        <slot />
      </p>
    </div>
  </div>
</template>

<script setup>
import { ExclamationIcon } from '@heroicons/vue/outline';
</script>

<style></style>
