<template>
  <div class="min-h-screen bg-grey-darker p-8">
    <div class="max-w-sm mx-auto card mt-8">
      <label class="form-label mb-2">Inline Tag Input</label>
      <stack-tag-input v-model="tags"></stack-tag-input>
    </div>
    <div class="max-w-sm mx-auto card mt-8">
      <label class="form-label mb-2">Inline Tag Input</label>
      <inline-tag-input v-model="tags"></inline-tag-input>
    </div>

    <div class="max-w-sm mx-auto card mt-8">
      <label class="form-label mb-2">Original Tag Input</label>
      <tag-input v-model="tags"></tag-input>
    </div>
  </div>
</template>

<script>
import InlineTagInput from "./components/InlineTagInput";
import StackTagInput from "./components/StackTagInput";
import TagInput from "./components/TagInput";

export default {
  name: "App",
  components: {
    TagInput,
    InlineTagInput,
    StackTagInput,
  },
  data() {
    return {
      tags: ["awesome", "excellent", "amazing"],
    };
  },
};
</script>

<style>
@import "./assets/css/app.css";
</style>
