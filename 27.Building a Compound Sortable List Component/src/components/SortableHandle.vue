<script>
export default {
  inject: ["sortableListHandle"],
  mounted() {
    this.$el.classList.add(this.sortableListHandle);
  },
  render() {
    return this.$slots.default[0];
  },
};
</script>