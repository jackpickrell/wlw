<script setup>

</script>

<template>
  <div class="mt-10">
    <p class="text-sm text-gray-700">
      Specify the details of your company or brand as you would like them to
      appear on your website. You can control where these are presented on your
      site in <a href="/navigation">Navigation & Appearance</a>.
    </p>
    <form class="mt-5">
      <div class="mb-5">
        <label for="title" class="label">Company, Trading or Brand Name</label>
        <input type="text" class="input" placeholder="ACME Corp" />
      </div>
      <div class="mb-5">
        <label for="title" class="label">Email Address</label>
        <input type="text" class="input" placeholder="info@acmecorp.com" />
      </div>
      <div class="mb-5">
        <label for="title" class="label">Telephone Number</label>
        <input type="text" class="input" placeholder="01234 567890" />
      </div>
      <div class="mb-5">
        <label for="address" class="label">Address</label>
        <textarea name="address" id="address" rows="5" class="input"></textarea>
      </div>
      <div class="flex justify-end">
        <button type="submit" class="btn-primary">Save Changes</button>
      </div>
    </form>
  </div>
</template>
