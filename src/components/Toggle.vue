<template>
  <SwitchGroup
    as="div"
    class="
      py-3 
      sm:py-4
      grid grid-cols-2
      sm:grid-cols-3
      gap-4
      items-center
    "
  >
    <SwitchLabel
      as="dt"
      class="text-sm font-medium text-gray-700 sm:col-span-2"
      passive
    >
      <slot />
    </SwitchLabel>
    <dd class="mt-1 flex text-sm text-gray-900 sm:mt-0">
      <Switch
        v-model="model"
        :class="[
          model ? 'bg-accent-500' : 'bg-gray-200',
          'relative inline-flex flex-shrink-0 h-6 w-11 border-2 border-transparent rounded-full cursor-pointer transition-colors ease-in-out duration-200 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-primary-500 ml-auto',
        ]"
      >
        <span
          aria-hidden="true"
          :class="[
            model ? 'translate-x-5' : 'translate-x-0',
            'inline-block h-5 w-5 rounded-full bg-white shadow transform ring-0 transition ease-in-out duration-200',
          ]"
        />
      </Switch>
    </dd>
  </SwitchGroup>
</template>

<script setup>
import { Switch, SwitchGroup, SwitchLabel } from '@headlessui/vue';
</script>

<script>
  export default {
    props: ['model'],
  };
</script>
