<script>
export default {
  props: ["contacts"],
  render() {
    return this.$scopedSlots.default({
      subject: "world",
    });

    // return createElement(
    //   "span",
    //   {
    //     class: "text-xl text-blue font-bold",
    //   },
    //   [
    //     this.$scopedSlots.default({
    //       subject: "world",
    //     }),
    //   ]
    // );
  },
};
</script>

<style scoped>
</style>