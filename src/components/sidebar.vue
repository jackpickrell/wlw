<script>
  export default {
    name: 'Sidebar',
    props: ['navigation', 'secondaryNavigation', 'currentRoute'],
    return: {}
  }
</script>

<template>
  <div class="hidden md:flex md:w-64 md:flex-col md:fixed md:inset-y-0">
    <nav
      class="
        bg-gray-50
        border-r border-gray-200
        pt-5
        pb-4
        flex flex-col flex-grow
        overflow-y-auto
      "
    >
      <div class="flex-shrink-0 px-4 flex items-center">
        <img
          class="h-8 w-auto"
          src="https://tailwindui.com/img/logos/easywire-logo-purple-600-mark-gray-900-text.svg"
          alt="Easywire"
        />
      </div>
      <div class="flex-grow mt-5">
        <div class="space-y-1">
          <a
            v-for="item in navigation"
            :key="item.name"
            :href="item.href"
            :class="[
              item.current
                ? 'bg-primary-500 text-white'
                : 'border-transparent text-gray-600 hover:text-gray-900 hover:bg-gray-50',
              'group border-l-4 py-2 px-3 flex items-center text-sm font-medium',
            ]"
          >
            <component
              :is="item.icon"
              :class="[
                item.current
                  ? 'text-white'
                  : 'text-gray-600 group-hover:text-gray-800',
                'mr-3 flex-shrink-0 h-6 w-6',
              ]"
              aria-hidden="true"
            />
            {{ item.name }}
          </a>
        </div>
      </div>
      <div class="flex-shrink-0 block w-full">
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
            text-sm
            font-medium
            text-gray-600
            hover:text-gray-900 hover:bg-gray-50
          "
        >
          <component
            :is="item.icon"
            class="text-gray-400 group-hover:text-gray-500 mr-3 h-6 w-6"
            aria-hidden="true"
          />
          {{ item.name }}
        </a>
      </div>
    </nav>
  </div>
</template>
