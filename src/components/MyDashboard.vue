<script>
import {
  CogIcon,
  CubeIcon,
  DocumentTextIcon,
  NewspaperIcon,
  QuestionMarkCircleIcon,
  TemplateIcon,
} from '@heroicons/vue/outline';

const actions = [
  {
    title: 'Manage Products & Categories',
    href: '#',
    icon: CubeIcon,
    description:
      'Choose which products, product types, brands and categories you wish to show on your website.',
  },
  {
    title: 'Edit Pages',
    href: '#',
    icon: DocumentTextIcon,
    description:
      'Amend the presentation and content of pages on your website, including home, about, contact and legal pages.',
  },
  {
    title: 'Adjust Navigation & Appearance',
    href: '#',
    icon: TemplateIcon,
    description:
      'Decide on what links and information are included in the header and footer of your website, change your logo and choose colours.',
  },
  {
    title: 'Other Settings',
    href: '#',
    icon: CogIcon,
    description:
      'Embed your website, add Google Tracking, change company details and manage billing.',
  },
  {
    title: "What's New?",
    href: '#',
    icon: NewspaperIcon,
    description:
      'See what’s changed since you last logged in.',
  },
  {
    title: 'Get Help',
    href: '#',
    icon: QuestionMarkCircleIcon,
    description:
      'Browse our help documentation and get answers to questions about how to setup your website.',
  },
];

export default {
  name: 'MyDashboad',
  setup() {
    return {
      actions,
    };
  },
};
</script>

<template>
  <div class="px-4 sm:px-6 md:px-0 text-gray-700 mb-8">
    <h1 class="text-3xl font-bold mb-2">Welcome to Your Catalogue</h1>
    <p>What do you want to do?</p>
  </div>
  <div
    class="
      rounded-lg
      bg-gray-200
      overflow-hidden
      shadow
      divide-y divide-gray-200
      sm:divide-y-0 sm:grid sm:grid-cols-2 sm:gap-px
    "
  >
    <div
      v-for="(action, actionIdx) in actions"
      :key="action.title"
      :class="[
        actionIdx === 0 ? 'rounded-tl-lg rounded-tr-lg sm:rounded-tr-none' : '',
        actionIdx === 1 ? 'sm:rounded-tr-lg' : '',
        actionIdx === actions.length - 2 ? 'sm:rounded-bl-lg' : '',
        actionIdx === actions.length - 1
          ? 'rounded-bl-lg rounded-br-lg sm:rounded-bl-none'
          : '',
        'relative group bg-white p-6 focus-within:ring-2 focus-within:ring-inset focus-within:ring-primary-500',
      ]"
    >
      <div>
        <span class="text-primary-500">
          <component :is="action.icon" class="h-8 w-8" aria-hidden="true" />
        </span>
      </div>
      <div class="mt-8">
        <h3 class="text-lg font-medium text-gray-700">
          <a :href="action.href" class="focus:outline-none">
            <!-- Extend touch target to entire panel -->
            <span class="absolute inset-0" aria-hidden="true" />
            {{ action.title }}
          </a>
        </h3>
        <p class="mt-2 text-sm text-gray-500">
          {{ action.description }}
        </p>
      </div>
      <span
        class="
          pointer-events-none
          absolute
          top-6
          right-6
          text-gray-300
          group-hover:text-gray-400
        "
        aria-hidden="true"
      >
        <svg
          class="h-6 w-6"
          xmlns="http://www.w3.org/2000/svg"
          fill="currentColor"
          viewBox="0 0 24 24"
        >
          <path
            d="M20 4h1a1 1 0 00-1-1v1zm-1 12a1 1 0 102 0h-2zM8 3a1 1 0 000 2V3zM3.293 19.293a1 1 0 101.414 1.414l-1.414-1.414zM19 4v12h2V4h-2zm1-1H8v2h12V3zm-.707.293l-16 16 1.414 1.414 16-16-1.414-1.414z"
          />
        </svg>
      </span>
    </div>
  </div>
</template>
