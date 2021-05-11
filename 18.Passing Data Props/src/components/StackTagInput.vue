<template>
  <renderless-tag-input
    @update="(newValue) => $emit('update', newValue)"
    :tags="tags"
  >
    <div
      class="stacked-tag-input"
      slot-scope="{ tags, inputProps, inputEvents, addTag, removeButtonEvents }"
    >
      <div class="stacked-tag-input-form">
        <input
          v-on="inputEvents"
          v-bind="inputProps"
          class="form-input"
          placeholder="Add tag..."
        />
        <button @click="addTag" class="btn btn-indigo">Add Tag</button>
      </div>
      <ul class="stacked-tag-list">
        <li v-for="tag in tags" :key="tag">
          {{ tag }}
          <button
            v-on="removeButtonEvents(tag)"
            type="button"
            class="stacked-tag-link"
          >
            Remove
          </button>
        </li>
      </ul>
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
  props: {
    tags: {
      required: true,
      type: Array,
    },
  },
  components: {
    RenderlessTagInput,
  },
};
</script>

<style scoped>
</style>