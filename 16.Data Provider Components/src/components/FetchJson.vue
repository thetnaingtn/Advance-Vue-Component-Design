<script>
export default {
  data() {
    return {
      json: null,
      loading: true,
    };
  },
  props: ["url"],
  created() {
    fetch(this.url)
      .then((response) => response.json())
      .then((data) => {
        this.loading = false;
        this.json = data.splice(0, 5);
      });
  },
  render() {
    return this.$scopedSlots.default({
      json: this.json,
      loading: this.loading,
    });
  },
};
</script>