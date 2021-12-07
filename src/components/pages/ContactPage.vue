<script setup>
  import { ref } from 'vue';
  import Tiptap from '../Tiptap.vue';
  import Toggle from '../Toggle.vue';

  const showPhone = ref(true);
  const showEmail = ref(true);
  const showAddress = ref(true);
  const published = ref(true);
</script>

<template>
  <div class="mt-10">
    <p class="text-sm text-gray-700">
      If you would like to include a information page about your business on
      your website, you can do so here
    </p>
    <form class="mt-5">
      <div class="mb-5">
        <label for="title" class="label">Page Title</label>
        <input
          type="text"
          class="input"
          placeholder="If left blank, this will default to 'Get in touch with <Your Business Name>'"
        />
      </div>
      <div class="mb-5">
        <label for="title" class="label">Page Content</label>
        <tiptap />
      </div>
      <Toggle model="showPhone">
        <p class="mb-2">Show Telephone Number</p>
        <p class="text-xs font-normal">
          Display the telephone number specified in your
          <a class="text-primary-500" href="/settings">settings</a>.
        </p>
      </Toggle>
      <Toggle model="showEmail">
        <p class="mb-2">Show Email Address</p>
        <p class="text-xs font-normal">
          Display the email address specified in your
          <a class="text-primary-500" href="/settings">settings</a>.
        </p>
      </Toggle>
      <Toggle model="showAddress">
        <p class="mb-2">Show Address</p>
        <p class="text-xs font-normal">
          Display the address specified in your
          <a class="text-primary-500" href="/settings">settings</a>.
        </p>
      </Toggle>
      <hr class="my-4 border-gray-500">
      <Toggle model="published">
        <p class="mb-2">Published</p>
        <p class="text-xs font-normal">
          You can choose if this page is included on your website. When
          unpublished, any links to this page in your header and footer will be
          hidden.
        </p>
      </Toggle>
      <div class="flex justify-end mt-4">
        <button type="submit" class="btn-primary">Save Changes</button>
      </div>
    </form>
  </div>
</template>
