<template>
  <div class="accordion-list">
    <slot></slot>
  </div>
</template>

<script>
export default {
  provide() {
    return {
      accordionListState: this.shareStates,
    };
  },
  data() {
    return {
      shareStates: {
        activeItem: 1,
      },
    };
  },
};
</script>