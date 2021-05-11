<template>
  <input
    :value="value"
    placeholder="YYYY-MM-DD"
    type="text"
    ref="datepicker"
    class="form-input"
  />
</template>

<script>
import Pickaday from "pikaday";

export default {
  name: "DatePicker",
  props: {
    value: { required: true },
    format: { default: "YYYY-MM-DD" },
    options: { default: {} },
  },
  mounted() {
    const picker = new Pickaday({
      field: this.$refs.datepicker,
      format: this.format,
      onSelect: () => {
        this.$emit("input", picker.toString());
      },
      ...this.options,
    });
  },
};
</script>

<style scoped>
</style>