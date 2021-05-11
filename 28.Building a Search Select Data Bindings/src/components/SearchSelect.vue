<template>
  <on-click-outside :on="close">
    <div class="search-select" :class="{ 'is-active': isOpen }">
      <button
        ref="button"
        @click="open"
        type="button"
        class="search-select-input"
      >
        <span v-if="value">{{ value }}</span>
        <span v-else class="search-select-placeholder">Select a band...</span>
      </button>
      <div ref="dropdown" v-show="isOpen" class="search-select-dropdown">
        <input
          ref="searchInput"
          v-model="search"
          class="search-select-search"
          @keydown.esc="close"
          @keydown.up="highlightPrev"
          @keydown.down="highlightNext"
          @keydown.enter.prevent="selectHighlighted"
          @keydown.tab.prevent
        />
        <ul ref="options" class="search-select-options">
          <li
            :class="{ 'is-active': index === highlightedIndex }"
            class="search-select-option"
            v-for="(option, index) in filteredOptions"
            :key="option"
            @click="select(option)"
          >
            {{ option }}
          </li>
        </ul>
        <div v-show="!filteredOptions.length" class="search-select-empty">
          No results found for "{{ search }}"
        </div>
      </div>
    </div>
  </on-click-outside>
</template>
<script>
import OnClickOutside from "./OnClickOutside";
import Popper from "popper.js";

export default {
  components: {
    OnClickOutside,
  },
  props: ["value", "options", "filterFunction"],
  data() {
    return {
      search: "",
      isOpen: false,
      highlightedIndex: 0,
    };
  },
  methods: {
    open() {
      if (this.isOpen) {
        return;
      }
      this.isOpen = true;
      this.$nextTick(() => {
        this.$refs.searchInput.focus();
        this.scrollToHighlighted();
        this.setUpPopper();
      });
    },
    setUpPopper() {
      if (this.popper === undefined) {
        this.popper = new Popper(this.$refs.button, this.$refs.dropdown, {
          placement: "bottom",
        });
      } else {
        this.popper.schduleUpdate();
      }
    },
    close() {
      this.isOpen = false;
    },
    select(option) {
      this.$emit("input", option);
      this.highlightedIndex = 0;
      this.$refs.button.focus();
      this.close();
    },
    scrollToHighlighted() {
      this.$refs.options.children[this.highlightedIndex].scrollIntoView({
        block: "nearest",
      });
    },
    highlight(index) {
      this.highlightedIndex = index;
      if (this.highlightedIndex > this.filteredOptions.length - 1) {
        this.highlightedIndex = 0;
      }

      if (this.highlightedIndex < 0) {
        this.highlightedIndex = this.filteredOptions.length - 1;
      }

      this.scrollToHighlighted();
    },

    highlightNext() {
      this.highlight(this.highlightedIndex + 1);
    },

    highlightPrev() {
      this.highlight(this.highlightedIndex - 1);
    },

    selectHighlighted() {
      let selected = this.filteredOptions[this.highlightedIndex];
      this.select(selected);
    },
  },
  computed: {
    filteredOptions() {
      return this.filterFunction(this.search, this.options);
    },
  },
};
</script>