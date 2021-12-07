<script setup>
  import { ref } from 'vue';
  import Toggle from '../Toggle.vue';

  const showPhone = ref(true);
  const showEmail = ref(true);
  const showAddress = ref(true);
  const published = ref(true);
</script>

<template>
  <div class="mt-10">
    <p class="text-sm text-gray-700">
      Customise the items that appear in your footer here. Any changes you make
      will take effect instantly.
    </p>
    <form class="mt-5">
      <Toggle model="showPhone">
        <p class="mb-2.5">Show Telephone Number</p>
        <p class="text-xs font-normal">
          Display the telephone number specified in your
          <a class="text-primary-500" href="/settings">settings</a>.
        </p>
      </Toggle>
      <Toggle model="showEmail">
        <p class="mb-2.5">Show Email Address</p>
        <p class="text-xs font-normal">
          Display the email address specified in your
          <a class="text-primary-500" href="/settings">settings</a>.
        </p>
      </Toggle>
      <Toggle model="showSearch">
        <p class="mb-2.5">Show Business Name</p>
        <p class="text-xs font-normal">
          Display the business name specified in your <a class="text-primary-500" href="/settings">settings</a>.
        </p>
      </Toggle>
      <Toggle model="showSearch">
        <p class="mb-2.5">Show Business Address</p>
        <p class="text-xs font-normal">
          Display the business address specified in your <a class="text-primary-500" href="/settings">settings</a>.
        </p>
      </Toggle>
      <Toggle model="showSearch">
        <p class="mb-2.5">Show Logo</p>
        <p class="text-xs font-normal">
          Display your company logo.
        </p>
      </Toggle>
      <Toggle model="showSearch">
        <p class="mb-2.5">Show Contact Page Link</p>
        <p class="text-xs font-normal">
          Display a link to your contact page.
        </p>
      </Toggle>
      <Toggle model="showSearch">
        <p class="mb-2.5">Show Legal Pages</p>
        <p class="text-xs font-normal">
          Display links to your Cookie, Privacy and Terms pages.
        </p>
      </Toggle>
      <Toggle model="showSearch">
        <p class="mb-2.5">Show About/Info Page Link</p>
        <p class="text-xs font-normal">
          Display a link to your about us page.
        </p>
      </Toggle>
      <Toggle model="showSearch">
        <p class="mb-2.5">Show Facebook Icon & Link</p>
        <p class="text-xs font-normal">
          Display a link to the Facebook profile specified in your <a class="text-primary-500" href="/settings">settings</a>.
        </p>
      </Toggle>
      <Toggle model="showSearch">
        <p class="mb-2.5">Show Twitter Icon & Link</p>
        <p class="text-xs font-normal">
          Display a link to the Twitter profile specified in your <a class="text-primary-500" href="/settings">settings</a>.
        </p>
      </Toggle>
      <Toggle model="showSearch">
        <p class="mb-2.5">Show Pinterest Icon & Link</p>
        <p class="text-xs font-normal">
          Display a link to the Pinterest profile specified in your <a class="text-primary-500" href="/settings">settings</a>.
        </p>
      </Toggle>
      <Toggle model="showSearch">
        <p class="mb-2.5">Show Instagram Icon & Link</p>
        <p class="text-xs font-normal">
          Display a link to the Instagram profile specified in your <a class="text-primary-500" href="/settings">settings</a>.
        </p>
      </Toggle>
      <Toggle model="showSearch">
        <p class="mb-2.5">Show Youtube Icon & Link</p>
        <p class="text-xs font-normal">
          Display a link to the Youtube profile specified in your <a class="text-primary-500" href="/settings">settings</a>.
        </p>
      </Toggle>
    </form>
  </div>
</template>
