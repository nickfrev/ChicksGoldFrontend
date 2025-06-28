<script setup lang="ts">
import CartIcon from 'vue-material-design-icons/Cart.vue'

defineProps<{
  item: {
    id: string
    isOnSale: boolean
    quantity: number
    name: string
    description: string
    price: number
    salePrice?: number
    gameLogo: string
    imageUrl: string
  }
}>()
</script>

<template>
  <div class="item">
    <!-- Sale notification -->
    <div class="on-sale-notif" :class="{ 'is-invisible': !item.isOnSale }">
      <span class="dot">• </span><span>ON SALE</span>
    </div>
    <div v-if="item.quantity > 0" class="stock-notif in-stock-notif">
      <span>In Stock</span>
    </div>
    <div v-else class="stock-notif no-stock-notif">
      <span>Sold Out</span>
    </div>

    <!-- Quantity Selector -->
    <div class="quantity-selector">
      <input type="number" min="1" :max="item.quantity" value="1" :disabled="item.quantity <= 0" />
    </div>

    <!-- Item Image -->
    <div>
      <img class="item-image" :src="item.imageUrl" alt="Item Image" />
    </div>

    <!-- Item Name -->
    <div class="item-name">
      <span>{{ item.name }}</span>
    </div>

    <!-- Item Price -->
    <div class="item-price">
      <span>${{ item.salePrice ?? item.price }}</span>
      <span v-if="item.salePrice" class="strike-out-price">
        <span>${{ item.price }}</span>
      </span>
    </div>

    <!-- Item Description -->
    <div class="item-description">
      <span>{{ item.description }}</span>
    </div>

    <!-- Buttons -->
    <div class="button-section">
      <button class="button-details">DETAILS</button>
      <button class="button-add">
        ADD
        <div class="button-add-icon"><CartIcon :size="18" /></div>
      </button>
    </div>
  </div>
</template>

<style scoped>
.is-invisible {
  visibility: hidden;
}

.item {
  position: relative;
  width: 210px;
  height: 300px;
  display: inline-block;
  background-color: #323648;
  border-radius: 5px;
  padding: 23px;
}

.on-sale-notif {
  font-size: 0.6rem;
  color: white;
}

.on-sale-notif > .dot {
  font-size: 0.8rem;
  color: #39e29d;
  font-weight: bold;
}

.stock-notif {
  font-size: 0.6rem;
  display: inline-block;
  border-radius: 4px;
  padding: 3px 10px;
  margin: 10px 0px;
}

.in-stock-notif {
  color: #39e29d;
  border: 1px solid #39e29d;
}

.no-stock-notif {
  color: #e23939;
  border: 1px solid #e23939;
}

.quantity-selector {
  position: absolute;
  top: 23px;
  right: 23px;
  width: 60px;
  height: 40px;
  display: inline-block;
}

.quantity-selector input {
  height: 100%;
  width: 100%;
  padding: 0px 5px 0px 10px;
  background-color: #373e54;
  border: none;
  border-radius: 5px;
  color: white;
}

.quantity-selector input:disabled {
  opacity: 0.5;
}

input[type='number']::-webkit-outer-spin-button,
input[type='number']::-webkit-inner-spin-button {
  -webkit-appearance: none;
  background: #373e54;
  opacity: 1;
}

.item-image {
  width: 55px;
  height: 55px;
  border: 1px solid #797979;
}

.item-name {
  margin: 10px 0px;
  font-size: 0.85rem;
}

.item-price {
  font-size: 0.75rem;
  font-weight: bold;
}

.strike-out-price {
  margin-left: 10px;
  text-decoration: line-through;
  text-decoration-thickness: 2px;
  color: #ff3636;
}
.strike-out-price > span {
  color: #c6c7cc;
}

.item-description {
  font-size: 0.6rem;
  line-height: 1rem;
  font-weight: 300;
  color: #a1a1a1;
  margin-top: 8px;
}

.button-section {
  margin-top: 15px;
  display: flex;
  justify-content: space-between;
}

.button-section button {
  height: 40px;
  border: none;
  border-radius: 5px;
  padding: 10px 10px;
  color: white;
  font-size: 0.8rem;
  font-weight: 300;
}

.button-details {
  background-color: #3c4053;
  opacity: 0.4;
  cursor: not-allowed;
}

.button-add {
  background-color: #5762d5;
  cursor: pointer;
}

.button-add:hover {
  background-color: #4d56bd;
}

.button-add-icon {
  display: inline-block;
  width: 35px;
  height: 30px;
  margin-top: -5px;
  margin-right: -5px;
  padding-top: 5px;
  vertical-align: middle;
  background-color: #454da8;
  border-radius: 5px;
}
</style>
