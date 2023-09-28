<script lang="ts" setup>
import { useCounterStore } from "@/stores/test.store";

const store = useCounterStore();
const client = useSupabaseClient();
const user = useSupabaseUser();

const email = ref("");
const password = ref("");

const authenticated = user.value;

const signUp = async () => {
  const { error } = await client.auth.signUp({
    email: email.value,
    password: password.value,
  });
  if (error) console.log(error);
};

// sign in function for the supabase client
const signIn = async () => {
  const { error } = await client.auth.signInWithPassword({
    email: email.value,
    password: password.value,
  });
  if (error) console.log(error);
};

// sign out function for the supabase client
const signOut = async () => {
  const { error } = await client.auth.signOut();
  if (error) console.log(error);
};
</script>
<template>
  <div>
    <h1 class="text-3xl font-bold underline">
      Hello world! {{ store.doubleCount }}
    </h1>
    <div v-if="!authenticated">
      <button @click="signUp">Sign up with user password</button>
      <input v-model="email" type="email" />
      <input v-model="password" type="password" />
      <button @click="signIn">Sign in</button>
    </div>
    <div v-else>
      <button @click="signOut">Sign Out</button>
    </div>
  </div>
</template>
