<script>
import {
  Dialog,
  DialogOverlay,
  Switch,
  SwitchGroup,
  SwitchLabel,
  TransitionChild,
  TransitionRoot,
} from '@headlessui/vue';

import { XIcon } from '@heroicons/vue/outline';

export default {
  name: 'MobileSidebar',
  props: ['navigation', 'secondaryNavigation', 'sidebarOpen'],
  components: {
    Dialog,
    DialogOverlay,
    Switch,
    SwitchGroup,
    SwitchLabel,
    TransitionChild,
    TransitionRoot,
    XIcon,
  },
};
</script>

<template>
  <TransitionRoot as="template" :show="sidebarOpen">
    <Dialog
      as="div"
      class="fixed inset-0 z-40 flex md:hidden"
      @close="sidebarOpen = false"
    >
      <TransitionChild
        as="template"
        enter="transition-opacity ease-linear duration-300"
        enter-from="opacity-0"
        enter-to="opacity-100"
        leave="transition-opacity ease-linear duration-300"
        leave-from="opacity-100"
        leave-to="opacity-0"
      >
        <DialogOverlay class="fixed inset-0 bg-gray-600 bg-opacity-75" />
      </TransitionChild>
      <TransitionChild
        as="template"
        enter="transition ease-in-out duration-300 transform"
        enter-from="-translate-x-full"
        enter-to="translate-x-0"
        leave="transition ease-in-out duration-300 transform"
        leave-from="translate-x-0"
        leave-to="-translate-x-full"
      >
        <div
          class="
            relative
            max-w-xs
            w-full
            bg-white
            pt-5
            pb-4
            flex-1 flex flex-col
          "
        >
          <TransitionChild
            as="template"
            enter="ease-in-out duration-300"
            enter-from="opacity-0"
            enter-to="opacity-100"
            leave="ease-in-out duration-300"
            leave-from="opacity-100"
            leave-to="opacity-0"
          >
            <div class="absolute top-0 right-0 -mr-14 p-1">
              <button
                type="button"
                class="
                  h-12
                  w-12
                  rounded-full
                  flex
                  items-center
                  justify-center
                  focus:outline-none focus:bg-gray-600
                "
                @click="sidebarOpen = false"
              >
                <XIcon class="h-6 w-6 text-white" aria-hidden="true" />
                <span class="sr-only">Close sidebar</span>
              </button>
            </div>
          </TransitionChild>
          <div class="flex-shrink-0 px-4 flex items-center">
            <img
              class="h-8 w-auto"
              src="https://tailwindui.com/img/logos/easywire-logo-purple-600-mark-gray-900-text.svg"
              alt="Easywire"
            />
          </div>
          <div class="mt-5 flex-1 h-0 overflow-y-auto">
            <nav class="h-full flex flex-col">
              <div class="space-y-1">
                <a
                  v-for="item in navigation"
                  :key="item.name"
                  :href="item.href"
                  :class="[
                    item.current
                      ? 'bg-purple-50 border-purple-600 text-purple-600'
                      : 'border-transparent text-gray-600 hover:bg-gray-50 hover:text-gray-900',
                    'group border-l-4 py-2 px-3 flex items-center text-base font-medium',
                  ]"
                  :aria-current="item.current ? 'page' : undefined"
                >
                  <component
                    :is="item.icon"
                    :class="[
                      item.current
                        ? 'text-purple-500'
                        : 'text-gray-400 group-hover:text-gray-500',
                      'mr-4 flex-shrink-0 h-6 w-6',
                    ]"
                    aria-hidden="true"
                  />
                  {{ item.name }}
                </a>
              </div>
              <div class="mt-auto pt-10 space-y-1">
                <a
                  v-for="item in secondaryNavigation"
                  :key="item.name"
                  :href="item.href"
                  class="
                    group
                    border-l-4 border-transparent
                    py-2
                    px-3
                    flex
                    items-center
                    text-base
                    font-medium
                    text-gray-600
                    hover:text-gray-900 hover:bg-gray-50
                  "
                >
                  <component
                    :is="item.icon"
                    class="mr-4 h-6 w-6 text-gray-400 group-hover:text-gray-500"
                    aria-hidden="true"
                  />
                  {{ item.name }}
                </a>
              </div>
            </nav>
          </div>
        </div>
      </TransitionChild>
      <div class="flex-shrink-0 w-14" aria-hidden="true">
        <!-- Dummy element to force sidebar to shrink to fit close icon -->
      </div>
    </Dialog>
  </TransitionRoot>
</template>
