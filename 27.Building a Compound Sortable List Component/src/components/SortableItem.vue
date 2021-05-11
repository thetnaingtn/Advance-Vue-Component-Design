<script>
export default {
  inject: ["sortableListItem"],
  mounted() {
    this.$el.classList.add(this.sortableListItem);
  },
  render() {
    console.log(this.$slots.default[0]);
    return this.$slots.default[0];
  },
};
</script>