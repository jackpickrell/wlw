<script setup>
  const embedCode =
    '<iframe src="https://fullcollection.com/" name="Full Collection Embed Code" scrolling="No" height="800px" width="100%" style="border: none;"></iframe>';
</script>

<script>
  export default {
    data() {
      return {
        copied: false,
      };
    },
    methods: {
      copyEmbedCode() {
        navigator.clipboard.writeText(this.embedCode).then(() => {
          this.copied = true;
          setTimeout(() => {
            this.copied = false;
          }, 1000);
        });
      },
    },
  };
</script>

<template>
  <div class="mt-10">
    <p class="text-sm text-gray-700">
      You can use the details below to embed your catalogue within another
      website, setup Google Analytics and configure a holding page message.
    </p>

    <form class="mt-5">
      <div class="mb-5 mt-5">
        <label for="embedCode" class="label">Embed Code</label>
        <div class="flex space-x-4">
          <textarea
            v-model="embedCode"
            name="serviceMessage"
            id="serviceMessage"
            rows="2"
            class="input font-mono text-gray-500"
            disabled
          ></textarea>
          <button
            @click="copyEmbedCode"
            type="button"
            class="btn-primary text-sm w-36"
          >
            {{ copied ? `Copied` : `Copy Code` }}
          </button>
        </div>
        <p class="text-xs mt-2.5">
          The code above will allow you to embed your catalogue into another
          website using an iFrame. Find out
          <a href="#">more about embedding</a>.
        </p>
      </div>
      <div class="mb-5 mt-5">
        <label for="serviceMessage" class="label"
          >Google Tag Manager (GTM) Code</label
        >
        <textarea name="gtm" id="gtm" rows="5" class="input"></textarea>
        <p class="text-xs mt-2.5">
          Paste your GTM code snippet into the field above to add GTM to your
          website pages. Find out
          <a href="https://developers.google.com/tag-manager/quickstart"
            >more about Google Tag Manager (GTM).</a
          >
        </p>
      </div>
      <div class="mb-5 mt-5">
        <label for="holdingMessage" class="label">Holding Page Message</label>
        <textarea
          name="holdingMessage"
          id="holdingMessage"
          rows="5"
          class="input"
          placeholder="Our website is currently being update. Please check back soon."
        ></textarea>
        <p class="text-xs mt-2.5">
          Customise the message that appears to visitors if your site is
          unpublished.
        </p>
      </div>
      <div class="flex justify-end">
        <button type="submit" class="btn-primary">Save Changes</button>
      </div>
    </form>
  </div>
</template>
