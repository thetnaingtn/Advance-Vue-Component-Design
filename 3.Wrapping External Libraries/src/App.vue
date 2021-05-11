<template>
  <div class="min-h-screen bg-grey-darker p-8">
    <div class="max-w-sm mx-auto">
      <div class="card">
        <label class="block">
          <span class="form-label mb-2">Select a date</span>
          <date-picker
            v-model="date"
            format="MMM D YYYY"
            :options="{ firstDay: 3 }"
          ></date-picker>
        </label>
      </div>
    </div>
  </div>
</template>

<script>
import DatePicker from "@/components/DatePicker";
export default {
  components: { DatePicker },
  data() {
    return {
      date: "Oct 17 2020",
    };
  },
};
</script>

<style>
@import "./assets/css/app.css";
@import "../node_modules/pikaday/css/pikaday.css";
</style>