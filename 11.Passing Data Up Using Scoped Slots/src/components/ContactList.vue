<template>
  <div class="card">
    <h1 class="text-2xl font-bold mb-6">Your Contacts</h1>
    <div>
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
            <slot name="email" :contact="contact">User's Email</slot>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      contacts: [],
    };
  },
  created() {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then((response) => response.json())
      .then((data) => {
        console.log(data);
        this.contacts = data.splice(0, 5);
      });
  },
};
</script>