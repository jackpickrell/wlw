<script setup>
  import { ref } from 'vue';
  import {
    RadioGroup,
    RadioGroupDescription,
    RadioGroupLabel,
    RadioGroupOption,
  } from '@headlessui/vue';
  import Toggle from '../Toggle.vue';

  const settings = [
    {
      name: 'Public access',
      description: 'This project would be available to anyone who has the link',
    },
    {
      name: 'Private to Project Members',
      description: 'Only members of this project would be able to access',
    },
    {
      name: 'Private to you',
      description: 'You are the only one able to access this project',
    },
  ];

  const selected = ref(settings[0]);
  const showBanners = ref(true);
  const copyArea = ref(false);
</script>

<template>
  <div class="mt-10">
    <p class="text-sm text-gray-700">
      If you would like to include an information page about your business on
      your website, you can do so here.
    </p>
    <form class="mt-5">
      <Toggle model="showBanners">
        <p class="mb-2.5">Show Marketing Banners</p>
        <p class="text-xs font-normal">
          When enabled, this will display promotional marketing banners created
          by PenCarrie on your website.
        </p>
      </Toggle>
      <div class="my-5">
        <p class="label">Product Category Thumbnails</p>
        <p class="text-xs text-gray-700">
          Choose the product categories you would like to appear on your
          homepage.
        </p>
      </div>
      <RadioGroup v-model="selected" class="mb-5">
        <!-- https://tailwindui.com/components/application-ui/forms/radio-groups -->

        <RadioGroupLabel class="sr-only"> Privacy setting </RadioGroupLabel>
        <div class="bg-white rounded-md -space-y-px">
          <RadioGroupOption
            as="template"
            v-for="(setting, settingIdx) in settings"
            :key="setting.name"
            :value="setting"
            v-slot="{ checked, active }"
          >
            <div
              :class="[
                settingIdx === 0 ? 'rounded-tl-md rounded-tr-md' : '',
                settingIdx === settings.length - 1
                  ? 'rounded-bl-md rounded-br-md'
                  : '',
                checked
                  ? 'bg-primary-50 border-primary-200 z-10'
                  : 'border-gray-200',
                'relative border p-4 flex items-center cursor-pointer focus:outline-none',
              ]"
            >
              <span
                :class="[
                  checked
                    ? 'bg-primary-600 border-transparent'
                    : 'bg-white border-gray-300',
                  active ? 'ring-2 ring-offset-2 ring-primary-500' : '',
                  'h-5 w-5 mt-0.5 cursor-pointer rounded-full border flex items-center justify-center',
                ]"
                aria-hidden="true"
              >
                <span class="rounded-full bg-white w-1.5 h-1.5" />
              </span>
              <div class="ml-2.5 flex flex-col">
                <RadioGroupLabel
                  as="span"
                  class="text-gray-900 block text-sm font-medium"
                >
                  {{ setting.name }}
                </RadioGroupLabel>
                <RadioGroupDescription
                  as="span"
                  class="text-gray-700 block text-sm"
                >
                  {{ setting.description }}
                </RadioGroupDescription>
              </div>
            </div>
          </RadioGroupOption>
        </div>
      </RadioGroup>
      <Toggle model="copyArea">
        <p class="mb-2">Homepage Copy Area</p>
        <p class="text-xs font-normal">
          When enabled, this will display promotional marketing banners created
          by PenCarrie on your website.
        </p>
      </Toggle>
    </form>
  </div>
</template>
