<script setup>
  import { ref } from 'vue';
  import Tiptap from '../Tiptap.vue';
  import Toggle from '../Toggle.vue';
  import Alert from '../Alert.vue';

  const published = ref(true);
</script>

<template>
  <div class="mt-10">
    <Alert>
      It is strongly recommended that you include a Cookie policy page on your
      website. We have provided some standardised content for this below, but
      you must review this wording to ensure it meets the needs of your
      business.
    </Alert>
    <form class="mt-5">
      <div class="mb-5">
        <label for="title" class="label">Page Content</label>
        <tiptap />
      </div>
      <Toggle model="published">
        <p class="mb-2">Published</p>
        <p class="text-xs font-normal">
          You can choose if this page is included on your website. When
          unpublished, any links to this page in your header and footer will be
          hidden.
        </p>
      </Toggle>
      <div class="flex justify-end">
        <button type="submit" class="btn-primary">Save Changes</button>
      </div>
    </form>
  </div>
</template>
