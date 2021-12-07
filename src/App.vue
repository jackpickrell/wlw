<script setup>
import { ref } from 'vue';
import {
  Dialog,
  DialogOverlay,
  Switch,
  SwitchGroup,
  SwitchLabel,
  TransitionChild,
  TransitionRoot,
} from '@headlessui/vue';
import {
  BellIcon,
  CogIcon,
  HomeIcon,
  MenuAlt2Icon,
  QuestionMarkCircleIcon,
  NewspaperIcon,
  CubeIcon,
  DocumentTextIcon,
  TemplateIcon,
  UserIcon,
} from '@heroicons/vue/outline';
import { SearchIcon } from '@heroicons/vue/solid';

import Dashboard from './components/Dashboard.vue';
import Sidebar from './components/MySidebar.vue';
import MobileSidebar from './components/MyMobileSidebar.vue';
import WhatsNew from './components/WhatsNew.vue';
import Products from './components/products/Index.vue';
import Pages from './components/pages/Index.vue';
import Navigation from './components/navigation/Index.vue';
import Settings from './components/settings/Index.vue';
import PublishBanner from './components/PublishBanner.vue';

const navigation = [
  { name: 'Dashboard', href: '/', icon: HomeIcon, current: true },
  { name: "What's New?", href: '/new', icon: NewspaperIcon, current: false },
  {
    name: 'Products & Categories',
    href: '/products',
    icon: CubeIcon,
    current: false,
  },
  { name: 'Pages', href: '/pages', icon: DocumentTextIcon, current: false },
  {
    name: 'Navigation & Appearance',
    href: '/navigation',
    icon: TemplateIcon,
    current: false,
  },
  { name: 'Settings', href: '/settings', icon: CogIcon, current: false },
];
const secondaryNavigation = [
  { name: 'Help', href: '/help', icon: QuestionMarkCircleIcon },
  { name: 'Logout', href: '#', icon: UserIcon },
];

const sidebarOpen = ref(false);
const published = false;
</script>

<script>
const routes = {
  '/': Dashboard,
  '/new': WhatsNew,
  '/products': Products,
  '/pages': Pages,
  '/navigation': Navigation,
  '/settings': Settings,
  '/help': WhatsNew,
};

export default {
  components: { PublishBanner },
  data() {
    return {
      currentRoute: window.location.pathname,
    };
  },
  computed: {
    CurrentComponent() {
      return routes[this.currentRoute];
    },
  },
};
</script>

<template>
  <div>
    <MobileSidebar
      :navigation="navigation"
      :secondary-navigation="secondaryNavigation"
      :sidebarOpen="sidebarOpen"
    />
    <Sidebar
      :navigation="navigation"
      :secondary-navigation="secondaryNavigation"
    />

    <PublishBanner :published="published" />

    <!-- Content area -->
    <div class="md:pl-64">
      <div class="max-w-4xl mx-auto flex flex-col md:px-8 xl:px-0">
        <div
          class="
            sticky
            top-0
            z-10
            flex-shrink-0
            h-16
            bg-white
            border-b border-gray-200
            flex
            md:hidden
          "
        >
          <button
            type="button"
            class="
              border-r border-gray-200
              px-4
              text-gray-500
              focus:outline-none
              focus:ring-2
              focus:ring-inset
              focus:ring-purple-500
            "
            @click="sidebarOpen = true"
          >
            <span class="sr-only">Open sidebar</span>
            <MenuAlt2Icon class="h-6 w-6" aria-hidden="true" />
          </button>
        </div>
        <main class="flex-1">
          <div class="relative max-w-4xl mx-auto md:px-8 xl:px-0">
            <div class="pt-10 pb-16">
              <component :is="CurrentComponent" />
            </div>
          </div>
        </main>
      </div>
    </div>
  </div>
</template>
