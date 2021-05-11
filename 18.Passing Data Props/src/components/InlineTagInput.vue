<template>
  <renderless-tag-input
    :tags="tags"
    @update="(newValue) => $emit('update', newValue)"
    :removeOnBackspace="true"
  >
    <div
      class="tag-input"
      slot-scope="{ tags, inputProps, removeButtonEvents, inputEvents }"
    >
      <span v-for="tag in tags" :key="tag" class="tag-input-tag">
        <span>{{ tag }}</span>
        <button
          type="button"
          v-on="removeButtonEvents(tag)"
          class="tag-input-remove"
        >
          &times;
        </button>
      </span>
      <input
        v-bind="inputProps"
        v-on="inputEvents"
        class="tag-input-text"
        placeholder="Add tag..."
      />
    </div>
  </renderless-tag-input>
</template>

<script>
import RenderlessTagInput from "./RenderlessTagInput";
export default {
  model: {
    prop: "tags",
    event: "update",
  },
  props: ["tags"],
  components: {
    RenderlessTagInput,
  },
};
</script>

<style scoped>
</style>