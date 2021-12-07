<script setup>
import { ref } from 'vue';
import { CheckIcon, ThumbUpIcon, UserIcon } from '@heroicons/vue/solid';
import Toggle from './Toggle.vue';

const timeline = [
  {
    id: 1,
    content: 'Applied to',
    target: 'Front End Developer',
    href: '#',
    date: 'Sep 20',
    datetime: '2020-09-20',
    icon: UserIcon,
    iconBackground: 'bg-gray-400',
  },
  {
    id: 2,
    content: 'Advanced to phone screening by',
    target: 'Bethany Blake',
    href: '#',
    date: 'Sep 22',
    datetime: '2020-09-22',
    icon: ThumbUpIcon,
    iconBackground: 'bg-blue-500',
  },
  {
    id: 3,
    content: 'Completed phone screening with',
    target: 'Martha Gardner',
    href: '#',
    date: 'Sep 28',
    datetime: '2020-09-28',
    icon: CheckIcon,
    iconBackground: 'bg-green-500',
  },
  {
    id: 4,
    content: 'Advanced to interview by',
    target: 'Bethany Blake',
    href: '#',
    date: 'Sep 30',
    datetime: '2020-09-30',
    icon: ThumbUpIcon,
    iconBackground: 'bg-blue-500',
  },
  {
    id: 5,
    content: 'Completed interview with',
    target: 'Katherine Snyder',
    href: '#',
    date: 'Oct 4',
    datetime: '2020-10-04',
    icon: CheckIcon,
    iconBackground: 'bg-green-500',
  },
];

const showDialog = ref(false);
const brand = ref(false);
</script>

<template>
  <div class="px-4 sm:px-6 md:px-0 text-gray-700 mb-8">
    <h1 class="text-3xl font-bold mb-2">Product & Site Updates</h1>
    <p>
      When new products or categories are available, we’ll tell you here so you
      can decide if you would like to include them on your site.
    </p>
  </div>
  <div class="rounded-lg border p-8 overflow-hidden shadow">
    <div class="flow-root">
      <ul role="list" class="-mb-8">
        <li v-for="(event, eventIdx) in timeline" :key="event.id">
          <div class="relative pb-8">
            <span
              v-if="eventIdx !== timeline.length - 1"
              class="absolute top-4 left-4 -ml-px h-full w-0.5 bg-gray-200"
              aria-hidden="true"
            />
            <div class="relative flex space-x-3">
              <div>
                <span
                  :class="[
                    event.iconBackground,
                    'h-8 w-8 rounded-full flex items-center justify-center ring-8 ring-white',
                  ]"
                >
                  <component
                    :is="event.icon"
                    class="h-5 w-5 text-white"
                    aria-hidden="true"
                  />
                </span>
              </div>
              <div class="min-w-0 flex-1 pt-1.5 flex justify-between space-x-4">
                <div>
                  <p class="text-sm text-gray-500">
                    {{ event.content }}
                    <a :href="event.href" class="font-medium text-gray-900">{{
                      event.target
                    }}</a>
                  </p>
                  <button
                    @click="showDialog = true"
                    class="text-sm text-primary-500"
                  >
                    View Details
                  </button>
                </div>
                <div class="text-right text-sm whitespace-nowrap text-gray-500">
                  <time :datetime="event.datetime">{{
                    new Date(event.datetime).toLocaleDateString()
                  }}</time>
                </div>
              </div>
            </div>
          </div>
        </li>
      </ul>
    </div>
  </div>
  <div v-if="showDialog">
    <div
      @click="showDialog = false"
      class="fixed inset-0 bg-black bg-opacity-50"
    ></div>
    <div class="fixed top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2">
      <div class="bg-white p-8 rounded-lg">
        <p class="text-gray-700 text-sm">
          The following brands are now available from PenCarrie. Choose which
          ones you want to include on your website.
        </p>
        <form>
          <Toggle model="brand">
            <p class="mb-2.5">Dickies</p>
          </Toggle>
          <div class="flex justify-end space-x-2">
            <button
              type="button"
              @click="showDialog = false"
              class="btn border-2 border-primary-500"
            >
              I'll decide later
            </button>
            <button
              type="submit"
              @click="showDialog = false"
              class="btn-primary"
            >
              Save & Close
            </button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>
