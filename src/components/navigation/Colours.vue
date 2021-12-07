<script setup>
  import Tiptap from '../Tiptap.vue';
  import Alert from '../Alert.vue';
  import ColorPicker from '../ColorPicker.vue';
</script>

<template>
  <div class="mt-10">
    <p class="text-sm text-gray-700 mb-5">
      Customise the the colours and logo here.
    </p>
    <form>
      <label for="cover-photo" class="label"> Upload a Logo </label>
      <div
        class="
          flex
          justify-center
          px-5
          py-5
          border-2 border-gray-300 border-dashed
          rounded-md
          mb-5
        "
      >
        <div class="space-y-1 text-center">
          <svg
            class="mx-auto h-12 w-12 text-gray-400"
            stroke="currentColor"
            fill="none"
            viewBox="0 0 48 48"
            aria-hidden="true"
          >
            <path
              d="M28 8H12a4 4 0 00-4 4v20m32-12v8m0 0v8a4 4 0 01-4 4H12a4 4 0 01-4-4v-4m32-4l-3.172-3.172a4 4 0 00-5.656 0L28 28M8 32l9.172-9.172a4 4 0 015.656 0L28 28m0 0l4 4m4-24h8m-4-4v8m-12 4h.02"
              stroke-width="2"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
          </svg>
          <div class="flex text-sm text-gray-600">
            <label
              for="file-upload"
              class="
                relative
                cursor-pointer
                bg-white
                rounded-md
                font-medium
                text-primary-500
                hover:text-primary-600
                focus-within:outline-none
                focus-within:ring-2
                focus-within:ring-offset-2
                focus-within:ring-primary-500
              "
            >
              <span>Upload a file</span>
              <input
                id="file-upload"
                name="file-upload"
                type="file"
                class="sr-only"
              />
            </label>
            <p class="pl-1">or drag and drop</p>
          </div>
          <p class="text-xs text-gray-500">PNG or JPG up to 3MB</p>
        </div>
      </div>
      <div class="grid sm:grid-cols-2 gap-5 items-center">
        <div class="py-5 text-gray-700">
          <p class="mb-2.5 text-sm font-medium">Header Colour</p>
          <p class="text-xs font-normal">
            The header is the main bar at the top of your website.
          </p>
        </div>
        <ColorPicker defaultColor="blue-100" />
      </div>
      <div class="grid sm:grid-cols-2 gap-5 items-center">
        <div class="py-5 text-gray-700">
          <p class="mb-2.5 text-sm font-medium">Footer Colour</p>
          <p class="text-xs font-normal">
            The footer is the bottom bar of your website.
          </p>
        </div>
        <ColorPicker />
      </div>
      <div class="grid sm:grid-cols-2 gap-5 items-center">
        <div class="py-5 text-gray-700">
          <p class="mb-2.5 text-sm font-medium">Primary Text Colour</p>
          <p class="text-xs font-normal">
            The primary colour of text on your website.
          </p>
        </div>
        <ColorPicker />
      </div>
      <div class="grid sm:grid-cols-2 gap-5 items-center">
        <div class="py-5 text-gray-700">
          <p class="mb-2.5 text-sm font-medium">Link Colour</p>
          <p class="text-xs font-normal">
            The colour for most links on your website.
          </p>
        </div>
        <ColorPicker />
      </div>
      <div class="grid sm:grid-cols-2 gap-5 items-center">
        <div class="py-5 text-gray-700">
          <p class="mb-2.5 text-sm font-medium">Link Hover Colour</p>
          <p class="text-xs font-normal">
            The colour links turn when hovered.
          </p>
        </div>
        <ColorPicker />
      </div>
      <div class="grid sm:grid-cols-2 gap-5 items-center">
        <div class="py-5 text-gray-700">
          <p class="mb-2.5 text-sm font-medium">Button Colour</p>
          <p class="text-xs font-normal">
            The primary colour for buttons on your website.
          </p>
        </div>
        <ColorPicker />
      </div>
      <div class="grid sm:grid-cols-2 gap-5 items-center">
        <div class="py-5 text-gray-700">
          <p class="mb-2.5 text-sm font-medium">Button Hover Colour</p>
          <p class="text-xs font-normal">
            The colour buttons turn when hovered.
          </p>
        </div>
        <ColorPicker />
      </div>

      <div class="flex justify-end mt-5">
        <button type="submit" class="btn-primary">Save Changes</button>
      </div>
    </form>
  </div>
</template>
