<template>
  <div class="container flex h-screen items-center justify-center">
    <div>
      <h1 class="text-2xl font-semibold">Welcome back</h1>
      <p>Click to log in</p>
      <UiButton external href="/api/auth/github">Login with Github</UiButton>
      <UiButton @click="getTestData">Get test data</UiButton>
    </div>
  </div>
</template>

<script lang="ts" setup>
  definePageMeta({
    middleware: "already-logged-in",
  });
  const getTestData = async () => {
    const { data, pending, error, refresh } = await useFetch("/api/auth/test", {});

    console.log(data.value);
  };
</script>
