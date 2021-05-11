<template>
  <div class="min-h-screen bg-grey-darker p-8">
    <div class="max-w-sm mx-auto">
      <contact-list>
        <template v-slot:email="{ contact }">
          <a :href="`mailto:${contact.email}`">
            {{ contact.email }}
          </a>
        </template>
      </contact-list>
    </div>
  </div>
</template>

<script>
import ContactList from "./components/ContactList";
export default {
  name: "App",
  components: {
    ContactList,
  },
};
</script>

<style>
@import "./assets/css/app.css";
</style>
