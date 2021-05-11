<template>
  <portal to="modals" v-if="show">
    <div class="modal-backdrop">
      <div class="modal">
        <slot></slot>
      </div>
    </div>
  </portal>
</template>

<script>
export default {
  props: ["show"],
  watch: {
    show: {
      handler(show) {
        if (show) {
          document.body.style.setProperty("overflow", "hidden")
        } else {
          document.body.style.removeProperty("overflow")
        }
      },
      immediate: true
    }
  },
  created() {
    const eventListener = (e) => {
      if (this.show && e.key === "Escape") {
        this.cancel()
      }
    }
    document.addEventListener("keydown", eventListener)
    this.$once("hook:destoryed", () => {
      document.removeEventListener(eventListener)
    })
  },
  methods: {
    cancel() {
      this.$emit("close")
    }
  }
}
</script>

<style scoped>
</style>