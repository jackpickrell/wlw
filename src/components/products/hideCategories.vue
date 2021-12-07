<script setup>
import Alert from '../Alert.vue';
import { Disclosure, DisclosureButton, DisclosurePanel } from '@headlessui/vue';
import { ChevronDownIcon } from '@heroicons/vue/outline';
import Toggle from '../Toggle.vue';

const sections = [
  {
    title: 'Product by Type',
    categories: [
      {
        title: 'Accessories',
        active: true,
        subCategories: [
          { title: 'Accessory Bags', active: true },
          { title: 'Arm Bands', active: true },
          { title: 'Belts, Braces, Straps & Chest Rig', active: true },
        ],
      },
      {
        title: 'Aprons',
        active: true,
        subCategories: [
          { title: 'Accessory Bags', active: true },
          { title: 'Arm Bands', active: true },
          { title: 'Belts, Braces, Straps & Chest Rig', active: true },
        ],
      },
    ],
  },
  {
    title: 'Product by Use',
    categories: [
      {
        title: 'Accessories',
        active: true,
        subCategories: [
          { title: 'Accessory Bags', active: true },
          { title: 'Arm Bands', active: true },
          { title: 'Belts, Braces, Straps & Chest Rig', active: true },
        ],
      },
      {
        title: 'Aprons',
        active: true,
        subCategories: [
          { title: 'Accessory Bags', active: true },
          { title: 'Arm Bands', active: true },
          { title: 'Belts, Braces, Straps & Chest Rig', active: true },
        ],
      },
    ],
  },
];
</script>

<template>
  <div class="mt-10">
    <p class="text-sm text-gray-700 mb-6">
      You can hide any categories that you don’t want to show on your website
      below. Click on one of the main headings below below to view available
      categories and subcategories and their visibility. Any changes you make
      will take effect instantly.
    </p>
    <Alert>
      Depending on your settings, some of the links used in marketing banners on
      the homepage may not work as expected.
    </Alert>
    <Disclosure
      as="div"
      v-for="section in sections"
      :key="section.title"
      class="pt-6"
      v-slot="{ open }"
    >
      <dt class="text-lg">
        <DisclosureButton
          class="
            text-left
            w-full
            flex
            justify-between
            items-start
            text-gray-400
          "
        >
          <span class="font-medium text-gray-900">
            {{ section.title }}
          </span>
          <span class="ml-6 h-7 flex items-center">
            <component
              :is="ChevronDownIcon"
              :class="[open ? '-rotate-180' : 'rotate-0', 'h-6 w-6 transform']"
              aria-hidden="true"
            />
          </span>
        </DisclosureButton>
      </dt>
      <DisclosurePanel as="dd" class="">
        <div v-for="category in section.categories" v-bind:key="category.title">
          <Toggle model="category.active">
            {{ category.title }}
          </Toggle>
          <div class="pl-6">
            <Toggle
              v-for="subCategory in category.subCategories"
              v-bind:key="subCategory.title"
              model="subCategory.active"
            >
              {{ subCategory.title }}
            </Toggle>
          </div>
        </div>
      </DisclosurePanel>
    </Disclosure>
  </div>
</template>
