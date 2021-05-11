<template>
  <div class="min-h-screen p-8">
    <div class="max-w-sm mx-auto">
      <hello-world>
        <strong slot-scope="{ subject }"> Hello {{ subject }} </strong>
      </hello-world>
    </div>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld";
export default {
  name: "App",
  components: {
    HelloWorld,
  },

  data() {
    return {
      contacts: [],
    };
  },

  created() {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then((response) => response.json())
      .then((res) => (this.contacts = res.splice(0, 5)));
  },
};
</script>

<style>
@import "./assets/css/app.css";
</style>
