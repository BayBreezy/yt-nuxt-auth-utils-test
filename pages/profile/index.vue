<template>
  <div>
    <h1>Welcome {{ user?.githubId }}</h1>

    <UiButton @click="logout">Logout</UiButton>

    <UiButton @click="getTestData">Get test data</UiButton>
  </div>
</template>

<script lang="ts" setup>
  const { loggedIn, user, session, clear } = useUserSession();

  const logout = async () => {
    await clear();
    navigateTo("/", { replace: true });
  };

  definePageMeta({
    middleware: "logged-in",
  });

  const getTestData = async () => {
    const { data, pending, error, refresh } = await useFetch("/api/auth/test", {});

    console.log(data.value);
  };
</script>
