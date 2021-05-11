<template>
  <span
    class="toggle flex-no-shrink"
    role="checkbox"
    tabindex="0"
    @click="toggle"
    @keydown.space.prevent="toggle"
    :aria-checked="toggled.toString()"
  ></span>
</template>

<script>
export default {
  props: ["toggled"],
  model: {
    prop: "toggled",
    event: "toggle",
  },
  methods: {
    toggle() {
      this.$emit("toggle", !this.toggled);
    },
  },
};
</script>

<style lang="scss" scoped>
</style>