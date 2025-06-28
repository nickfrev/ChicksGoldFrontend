<script setup lang="ts">
import CartIcon from 'vue-material-design-icons/Cart.vue'
</script>

<template>
  <button>
    <CartIcon />
    <span class="text">Cart (5)</span>
  </button>
</template>

<style scoped>
button {
  margin: 0px 10px;
  font-family: 'Montserrat', sans-serif;
  font-weight: 750;
  font-size: 0.8rem;
  background-color: rgba(0, 0, 0, 0);
  color: white;
  border: none;
  padding: 0.5rem 1rem;
  border-radius: 4px;
  cursor: pointer;
  text-transform: uppercase;
  font-weight: 500;
  height: 40px;
  vertical-align: middle;
  margin-top: -3px;
}

button:hover {
  background-color: rgba(0, 0, 0, 0.25);
}

.text {
  margin-right: 10px;
  margin-top: -7px;
  vertical-align: middle;
  display: inline-block;
  height: 100%;
}
</style>
