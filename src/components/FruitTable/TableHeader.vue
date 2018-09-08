<template>
  <div class="header">
    <div class="header--item">
      <span>Fruits</span>
    </div>
    <div class="header--item">
      <title-with-sorting-arrows :sort-method="onClickSortPrice">
        <span slot-scope="{handleClick}" @click="handleClick">Price</span>
      </title-with-sorting-arrows>
    </div>
    <div class="header--item">
      <title-with-sorting-arrows :sort-method="onClickSortStock">
        <span slot-scope="{handleClick}" @click="handleClick">Stock</span>
      </title-with-sorting-arrows>
    </div>
  </div>
</template>

<script>
import { mapMutations } from "vuex";
import TitleWithSortingArrows from "./TitleWithSortingArrows.vue";

export default {
  name: "TableHeader",
  components: { TitleWithSortingArrows },
  methods: {
    ...mapMutations({
      SORT_FRUITS: "SORT_FRUITS"
    }),
    onClickSortPrice(sortAscend) {
      const self = this;
      return (function applySortBy(sortBy) {
        self.SORT_FRUITS({ sortAscend, sortBy });
      })("price");
    },
    onClickSortStock(sortAscend) {
      const self = this;
      return (function applySortBy(sortBy) {
        self.SORT_FRUITS({ sortAscend, sortBy });
      })("stock");
    }
  }
};
</script>

<style scoped>
.header {
  height: 30px;
  width: 600px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  font-size: 12px;
  font-weight: bold;
  color: orange;
  border-bottom: 1px solid lightgrey;
  margin-bottom: 8px;
}
.header--item:not(-1) {
  flex: 1;
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;
}
</style>
