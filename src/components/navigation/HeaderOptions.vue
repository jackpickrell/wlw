<script setup>
  import { ref } from 'vue';
  import Toggle from '../Toggle.vue';

  const showPhone = ref(true);
  const showEmail = ref(true);
  const showSearch = ref(true);
  const showContact = ref(true);
  const showAbout = ref(true);
</script>

<template>
  <div class="mt-10">
    <p class="text-sm text-gray-700">
      Customise the items that appear in your header here. Any changes you make
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
        <p class="mb-2.5">Show Search Box</p>
        <p class="text-xs font-normal">
          Display the search box in your header.
        </p>
      </Toggle>
      <Toggle model="showContact">
        <p class="mb-2.5">Show Contact Page Link</p>
        <p class="text-xs font-normal">
          Display a link to your contact page.
        </p>
      </Toggle>
      <Toggle model="showAbout">
        <p class="mb-2.5">Show About/Info Page Link</p>
        <p class="text-xs font-normal">
          Display a link to your about us page.
        </p>
      </Toggle>
      <div class="mb-5 mt-5">
        <label for="serviceMessage" class="label">Service Message</label>
        <textarea name="serviceMessage" id="serviceMessage" rows="5" class="input"></textarea>
        <p class="text-xs mt-2.5">Use this to add an optional service message in your header.</p>
      </div>
    </form>
  </div>
</template>
