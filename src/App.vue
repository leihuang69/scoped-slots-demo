<template>
  <div id="app">
    <fruit-table ></fruit-table>
  </div>
</template>

<script>
import FruitTable from "./components/FruitTable";
import Vuex from "vuex";
import Vue from "vue";

import { descend, ascend, sortWith, prop } from "ramda";
const sortBy = options => prop(options.sortBy);

Vue.use(Vuex);
Vue.filter("capitalize", str => str.charAt(0).toUpperCase() + str.slice(1));
Vue.filter("addCurrency", (amount, currency) => `${currency} ${amount}`);

const store = () =>
  new Vuex.Store({
    state: {
      fruits: [
        { name: "bananas", price: 12, stock: 30 },
        { name: "apples", price: 16, stock: 25 },
        { name: "pineapples", price: 15, stock: 32 },
        { name: "oranges", price: 10, stock: 34 },
        { name: "pears", price: 13, stock: 60 },
        { name: "avocado", price: 20, stock: 50 }
      ]
    },
    mutations: {
      SORT_FRUITS(state, sortOptions) {
        const sortData = sortOptions.sortAscend
          ? sortWith([ascend(sortBy(sortOptions))])
          : sortWith([descend(sortBy(sortOptions))]);
        const sortedFruits = sortData(state.fruits);
        state.fruits = [...sortedFruits];
      }
    }
  });

export default {
  name: "app",
  store,
  components: {
    FruitTable
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
