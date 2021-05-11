<template>
  <div class="min-h-screen bg-grey-darker p-8">
    <div class="max-w-sm mx-auto">
      <fetch-json
        v-slot:default="{ json: contacts, loading }"
        url="https://jsonplaceholder.typicode.com/users"
      >
        <div class="card">
          <h1 class="text-2xl font-bold mb-6">Your Contacts</h1>
          <span v-if="loading">loading...</span>
          <div v-else>
            <div
              v-for="contact in contacts"
              :key="contact.id"
              class="flex items-center spaced-y-6"
            >
              <img
                src="https://cdn4.iconfinder.com/data/icons/avatars-xmas-giveaway/128/batman_hero_avatar_comics-512.png"
                class="h-12 w-12 rounded-full block mr-2"
                alt="batman"
              />
              <div>
                <div class="font-bold">
                  {{ contact.username }}
                </div>
                <div class="text-grey-dark">
                  <span>{{ contact.email }}</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </fetch-json>
    </div>
  </div>
</template>

<script>
import FetchJson from "./components/FetchJson";
export default {
  name: "App",
  components: {
    FetchJson,
  },
};
</script>

<style>
@import "./assets/css/app.css";
</style>
