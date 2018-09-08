<template>
  <div class="title">
    <div class="title--text">
      <slot :handleClick="onClickTitle"></slot>
    </div>
    <div class="title--arrows">
      <div :class="upArrowHighlighted ? 'up-arrow__highlight' : 'up-arrow'"
        @click="onClickUpArrow"></div>
      <div :class="downArrowHighlighted ? 'down-arrow__highlight' : 'down-arrow'"
        @click="onClickDownArrow"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "titleWithSortingArrows",
  props: ["sortMethod"],
  data() {
    return {
      sortTriggered: false,
      sortAscend: true
    };
  },
  computed: {
    upArrowHighlighted: function() {
      return this.sortTriggered && this.sortAscend;
    },
    downArrowHighlighted: function() {
      return this.sortTriggered && !this.sortAscend;
    }
  },
  methods: {
    checkIfSortTriggered() {
      if (!this.sortTriggered) {
        this.sortTriggered = true;
      }
    },
    onClickUpArrow() {
      this.sortMethod(true);
      this.sortAscend = true;
      this.checkIfSortTriggered();
    },
    onClickDownArrow() {
      this.sortMethod(false);
      this.sortAscend = false;
      this.checkIfSortTriggered();
    },
    onClickTitle() {
      this.sortMethod(!this.sortAscend);
      this.sortAscend = !this.sortAscend;
      this.checkIfSortTriggered();
    }
  }
};
</script>

<style scoped>
.title {
  height: 12px;
  display: flex;
  flex-direction: row;
  align-items: center;
  cursor: pointer;
}

.title--text {
  text-align: left;
  margin-right: 10px;
}

.title--arrows {
  margin-left: 3px;
  width: 10px;
  height: 20px;
  font-size: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
}

.up-arrow {
  width: 0;
  height: 0;
  border-style: solid;
  border-width: 0 8px 8px 8px;
  border-color: transparent transparent lightgrey transparent;
}

.up-arrow__highlight {
  width: 0;
  height: 0;
  border-style: solid;
  border-width: 0 8px 8px 8px;
  border-color: transparent transparent yellowgreen transparent;
}

.down-arrow {
  width: 0;
  height: 0;
  border-style: solid;
  border-width: 8px 8px 0 8px;
  border-color: lightgray transparent transparent transparent;
}

.down-arrow__highlight {
  width: 0;
  height: 0;
  border-style: solid;
  border-width: 8px 8px 0 8px;
  border-color: yellowgreen transparent transparent transparent;
}
</style>
