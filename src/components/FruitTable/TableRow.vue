<template functional>
    <div class="row">
        <div class="row--item">{{props.rowData.name | capitalize}}</div>
        <div class="row--item">{{props.rowData.price | addCurrency("￥")}}</div>
        <div class="row--item">{{props.rowData.stock}}</div>
    </div>
</template>

<style scoped>
.row {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  width: 600px;
}
.row--item {
  flex: 1;
}
.row--item:first-child {
  text-align: left;
}
.row--item:last-child {
  text-align: right;
}
</style>

