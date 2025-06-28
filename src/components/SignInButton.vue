<script setup lang="ts">
import AccountCowboyHatIcon from 'vue-material-design-icons/AccountCowboyHat.vue'
</script>

<template>
  <button>
    <span class="text">Sign In</span>
    <AccountCowboyHatIcon />
  </button>
</template>

<style scoped>
button {
  margin: 0px 10px;
  font-family: 'Montserrat', sans-serif;
  font-weight: 750;
  font-size: 0.8rem;
  background-color: #39e29d;
  color: #303141;
  border: none;
  padding: 0.5rem 1rem;
  border-radius: 4px;
  cursor: pointer;
  text-transform: uppercase;
  font-weight: 600;
  height: 40px;
  vertical-align: middle;
  margin-top: -3px;
}

button:hover {
  background-color: #32c28a;
}

.text {
  margin-right: 10px;
  margin-top: -7px;
  vertical-align: middle;
  display: inline-block;
  height: 100%;
}
</style>
