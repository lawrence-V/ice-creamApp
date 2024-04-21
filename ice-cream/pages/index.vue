<template>
  <v-layout>
    <v-app-bar> </v-app-bar>
    <v-main
      class="d-flex align-center justify-center"
      style="min-height: 300px"
    >
      <div class="container">
        <div class="left">
          <Control :cart="cart" :items="items" @addor-remove-cart="addtoCart" />
        </div>
        <div class="right">
          <Icecream :icecream="cart" />
        </div></div
    ></v-main>
  </v-layout>
</template>

<script setup>
const items = ref([
  { id: 1, name: "Chocolate", price: 2.5 },
  { id: 2, name: "Vanilla", price: 2 },
  { id: 3, name: "Strawberry", price: 3 },
  { id: 4, name: "orange", price: 2.5 },
]);

const cart = ref([]);

const addtoCart = (item) => {
  if (item.type === "add") {
    cart.value.push(item.item);
  } else if (item.type === "submit") {
    alert("Your total price is " + item.item);
    cart.value = [];
  } else {
    let position = cart.value.findIndex(
      (variant) => variant.id === item.item.id
    );
    cart.value.splice(position, 1);
  }
};
</script>

<style  scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 90vw;
}

.left {
  margin-left: 50px;
  flex-grow: 1;
}

.right {
  flex-grow: 2;
}
</style>