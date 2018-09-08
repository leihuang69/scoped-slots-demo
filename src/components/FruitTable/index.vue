<template>
  <div>
    <table-header/>
    <table-row v-for="fruit in $store.state.fruits" :key="fruit.name" :row-data="fruit" />
  </div>
</template>

<script>
import TableHeader from "./TableHeader.vue";
import TableRow from "./TableRow.vue";

export default {
  name: "Table",
  components: {
    TableHeader,
    TableRow
  }
};
</script>
