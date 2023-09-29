<script lang="ts" setup>
import brandSidebar from "~/components/tailwindUI/application-ui/application-shells/sidebar/brand_sidebar_with_light_header.vue";

definePageMeta({
  middleware: "auth",
});
</script>

<template>
  <div>
    <brandSidebar />
  </div>
</template>

<style scoped></style>
