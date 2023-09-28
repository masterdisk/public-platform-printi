<script lang="ts" setup>
const client = useSupabaseClient();

const signOut = async () => {
  const { error } = await client.auth.signOut();
  if (error) console.log(error);
  else navigateTo("/login");
};

definePageMeta({
  middleware: "auth",
});
</script>

<template>
  <div>
    <h2 class="text-blue-700">Dashboard</h2>
    <button @click="signOut">Sign Out</button>
  </div>
</template>

<style scoped></style>
