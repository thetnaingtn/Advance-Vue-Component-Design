<script>
import { Sortable } from "@shopify/draggable";
function move(items, oldIndex, newIndex) {
  const itemRemovedArray = [
    ...items.slice(0, oldIndex),
    ...items.slice(oldIndex + 1, items.length),
  ];

  return [
    ...itemRemovedArray.slice(0, newIndex),
    items[oldIndex],
    ...itemRemovedArray.slice(newIndex, itemRemovedArray.length),
  ];
}
export default {
  props: {
    value: { required: true },
    listItem: {
      default: "sortable-list-item",
    },
    listHandle: {
      default: "sortable-list-handle",
    },
  },
  provide() {
    return {
      sortableListItem: this.listItem,
      sortableListHandle: this.listHandle,
    };
  },
  mounted() {
    new Sortable(this.$el, {
      draggable: `.${this.listItem}`,
      handle: `.${this.listHandle}`,
      mirror: {
        constrainDimensions: true,
      },
    }).on("sortable:stop", ({ oldIndex, newIndex }) => {
      this.$emit("input", move(this.value, oldIndex, newIndex));
    });
  },
  render() {
    return this.$slots.default[0];
  },
};
</script>