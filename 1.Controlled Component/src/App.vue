<template>
  <div class="min-h-screen bg-grey-darker p-8">
    <div class="max-w-sm mx-auto">
      <user-setting></user-setting>
    </div>
  </div>
</template>

<script>
import UserSetting from "./components/UserSetting";
export default {
  name: "App",
  components: {
    UserSetting,
  },
};
</script>

<style>
@import "./assets/css/app.css";
</style>
