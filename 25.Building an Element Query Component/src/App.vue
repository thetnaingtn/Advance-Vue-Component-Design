<template>
  <div class="min-h-screen bg-grey-darker p-4">
    <div
      style="width: 420px"
      class="mx-auto border-l border-r border-dashed border-grey-dark py-4 mb-4"
    >
      <profile-card></profile-card>
    </div>
    <div
      style="width: 300px"
      class="mx-auto border-l border-r border-dashed border-grey-dark py-4 mb-4"
    >
      <profile-card></profile-card>
    </div>
  </div>
</template>

<script>
import ProfileCard from "./components/ProfileCard";
export default {
  name: "App",
  components: {
    ProfileCard,
  },
};
</script>

<style>
@import "./assets/css/app.css";
</style>
