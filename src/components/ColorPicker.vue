<template>
  <!-- I've built this to use Tailwind colors and input their values in the field, but I don't think this is a great method. We'll probably need a map of rgb values instead. -->
  <div class="flex relative justify-end">
    <input
      id="color-picker"
      class="border border-gray-400 p-2 rounded-lg"
      v-model="currentColor"
    />
    <div
      @click="isOpen = !isOpen"
      class="cursor-pointer rounded-full ml-3 my-auto h-10 w-10 flex"
      :class="`bg-${currentColor}`"
    ></div>
    <div
      v-show="isOpen"
      class="
        border border-gray-300
        origin-top-right
        absolute
        right-0
        top-full
        mt-2
        rounded-md
        shadow-lg
        z-10
      "
    >
      <div class="rounded-md bg-white shadow-xs p-2">
        <div class="flex">
          <template :key="color" v-for="color in colors">
            <div>
              <template v-for="variant in variants" :key="variant">
                <div
                  @click="selectColor(color, variant)"
                  class="cursor-pointer w-6 h-6 rounded-full mx-1 my-1"
                  :class="`bg-${color}-${variant}`"
                ></div>
              </template>
            </div>
          </template>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
const colors = [
  'gray',
  'red',
  'yellow',
  'green',
  'blue',
  'indigo',
  'purple',
  'pink',
];
const variants = [100, 200, 300, 400, 500, 600, 700, 800, 900];
</script>

<script>
export default {
  props: ['defaultColor'],
  data() {
    return {
      isOpen: false,
      currentColor: this.defaultColor || 'blue-400',
    };
  },
  methods: {
    selectColor(color, variant) {
      this.currentColor = color + '-' + variant;
      this.isOpen = false;
    },
  },
};
</script>
