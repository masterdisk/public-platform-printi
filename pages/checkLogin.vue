<script lang="ts" setup>
const client = useSupabaseClient();
const user = useSupabaseUser();

if (user.value) {
  console.log(user.value);
}

const signOut = async () => {
  const { error } = await client.auth.signOut();
  if (error) console.log(error);
};
</script>

<template>
  <div>
    <button @click="signOut">Sign Out</button>
  </div>
</template>

<style scoped></style>
