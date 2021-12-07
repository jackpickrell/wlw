<script>
import HeaderOptions from './MyHeaderOptions.vue';
import FooterOptions from './MyFooterOptions.vue';
import Colours from './MyColours.vue';

const tabs = [
  { name: 'Header Options', component: HeaderOptions },
  { name: 'Footer Options', component: FooterOptions },
  { name: 'Colours & Logo', component: Colours },
];

export default {
  setup() {
    return {
      tabs,
    };
  },
  data() {
    return {
      currentTab: tabs[0],
    };
  },
};
</script>

<template>
  <div class="px-4 sm:px-6 md:px-0 text-gray-700 mb-8">
    <h1 class="text-3xl font-bold mb-2">Navigation & Appearance</h1>
    <p>
      Use the tabs below to specify what information you would like to show on
      your website, upload a logo and choose colours.
    </p>
  </div>

  <div class="px-4 sm:px-6 md:px-0">
    <div class="py-6">
      <!-- Tabs -->
      <div class="lg:hidden">
        <label for="selected-tab" class="sr-only">Select a tab</label>
        <select
          id="selected-tab"
          name="selected-tab"
          class="
            mt-1
            block
            w-full
            pl-3
            pr-10
            py-2
            text-base
            border-gray-300
            focus:outline-none focus:ring-primary-500 focus:border-primary-500
            sm:text-sm
            rounded-md
          "
        >
          <option
            v-for="tab in tabs"
            :key="tab.name"
            :selected="tab == currentTab"
          >
            {{ tab.name }}
          </option>
        </select>
      </div>
      <div class="hidden lg:block">
        <div class="border-b border-gray-200">
          <nav class="-mb-px flex space-x-8">
            <a
              v-for="tab in tabs"
              :key="tab.name"
              @click="currentTab = tab"
              :class="[
                currentTab.name == tab.name
                  ? 'border-primary-500 text-primary-600'
                  : 'border-transparent text-gray-500 hover:border-gray-300 hover:text-gray-700',
                'whitespace-nowrap py-4 px-1 border-b-2 font-medium text-sm cursor-pointer',
              ]"
            >
              {{ tab.name }}
            </a>
          </nav>
        </div>
      </div>
      <!-- Dynamically change component on tab click -->
      <component :is="currentTab.component"></component>
    </div>
  </div>
</template>
