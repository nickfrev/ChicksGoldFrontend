<script setup lang="ts">
import ItemBrowserResults from './ItemBrowserResults.vue'
import SwordIcon from 'vue-material-design-icons/Sword.vue'
import MagnifyIcon from 'vue-material-design-icons/Magnify.vue'
import SackIcon from 'vue-material-design-icons/Sack.vue'
import FeatherIcon from 'vue-material-design-icons/Feather.vue'
import IconDropDown from './IconDropDown.vue'

import { ref } from 'vue'

const weaponURLS = import.meta.glob('@/assets/images/items/**/*.png', {
  eager: true,
  import: 'default',
})
const weaponNames = Object.keys(weaponURLS)

const items = ref([])

// generate random items
function getWeaponNameFromImageURL(imageURL) {
  const weaponName = imageURL.split('/').pop()?.split('.')[0].replace('-', ' ') || `Weapon ${i + 1}`

  return weaponName
    .split(' ')
    .map((word) => {
      if (word.length === 0) {
        return '' // Handle empty strings if present
      }
      return word.charAt(0).toUpperCase() + word.slice(1)
    })
    .join(' ')
}

for (let i = 0; i < 208; i++) {
  const weaponImageURL = weaponNames[Math.floor(Math.random() * weaponNames.length)]
  const weaponName = getWeaponNameFromImageURL(weaponImageURL)
  const newItem = {
    id: `item-${i}`,
    isOnSale: Math.random() > 0.5,
    quantity: Math.floor(Math.random() * 5),
    name: weaponName,
    description: `Lorem ipsum dolor sit amet consetetur sadipscing elitr.`,
    price: (Math.random() * 3000).toFixed(2),
    gameLogo: `https://picsum.photos/200/100?random=${i}`,
    imageUrl: weaponURLS[weaponImageURL],
  }
  newItem.salePrice = newItem.isOnSale ? (Math.random() * newItem.price).toFixed(2) : undefined
  items.value.push(newItem)
}
</script>

<template>
  <h1>Condimentum consectetur</h1>
  <div class="search-control">
    <!-- Game filter dropdown -->
    <div class="search-dropdowns">
      <IconDropDown
        class="game-filter-dropdown glass"
        title="Select a Game"
        :options="[
          {},
          { value: 'gmod', label: 'GMod' },
          { value: 'halo', label: 'Halo' },
          { value: 'runescape', label: 'Runescape' },
        ]"
      >
        <template v-slot:icon>
          <SwordIcon class="sword-icon" />
        </template>
      </IconDropDown>
    </div>

    <!-- Search Bar -->
    <div class="search-bar glass">
      <div class="magnifying-glass">
        <MagnifyIcon />
      </div>
      <div class="search-input-container">
        <input type="text" placeholder="Search" class="search-input" />
      </div>
    </div>

    <!-- Side Dropdowns -->
    <div class="search-dropdowns">
      <IconDropDown
        class="side-filter-dropdown glass"
        title="Price"
        :options="[
          { value: 'all', label: 'All', default: true },
          { value: 'cheap', label: 'Cheapo' },
          { value: 'expensive', label: 'Expensivo' },
        ]"
      >
        <template v-slot:icon>
          <SackIcon class="side-icon" />
        </template>
      </IconDropDown>
      <IconDropDown
        class="side-filter-dropdown glass"
        title="Item Type"
        :options="[
          { value: 'all', label: 'All', default: true },
          { value: 'weapon', label: 'Weapon' },
          { value: 'armor', label: 'Armor' },
        ]"
      >
        <template v-slot:icon>
          <FeatherIcon class="side-icon" />
        </template>
      </IconDropDown>
    </div>
  </div>

  <ItemBrowserResults :showAmount="20" :items="items" />
</template>

<style scoped>
h1 {
  font-size: 2.5rem;
}

.search-control {
  margin: 15px 0 20px 0;
  display: flex;
  flex-wrap: wrap;
  align-items: stretch;
  justify-content: center;
  gap: 20px;
}

.sword-icon {
  color: white;
}

.side-icon {
  color: #39e29d;
}

.glass {
  background-color: rgba(73, 91, 126, 0.2);
}

.search-dropdowns {
  display: inline-block;
  flex: 1;
}

.side-filter-dropdown {
  width: 150px;
}

.game-filter-dropdown {
  border-radius: 5px;
  width: 300px;
}

.search-bar {
  display: inline-block;
  position: relative;
  min-width: 300px;
  height: 50px;
  border-radius: 5px;
  line-height: 50px;
  flex: 2;
}

.magnifying-glass {
  display: inline-block;
  position: absolute;
  left: 0px;
  top: 0px;
  bottom: 0px;
  width: 50px;
  height: 50px;

  padding-top: 8px;
  padding-left: 20px;
}

.search-input-container {
  display: inline-block;

  position: absolute;
  left: 50px;
  right: 0px;
  top: 0px;
  bottom: 0px;
  height: 50px;
}

.search-input-container input {
  width: 100%;
  height: 100%;
  background-color: transparent;
  border: none;
  color: white;
  font-size: 1rem;
}

::placeholder {
  color: rgb(187, 187, 187);
  font-size: 0.9rem;
  opacity: 1; /* Firefox */
}

@media (width <= 1260px) {
  .search-bar {
    order: -1;
    width: 100%;
    flex: auto;
  }

  .search-dropdowns {
    flex: auto;
    text-align: center;
    margin-bottom: 10px;
  }

  .game-filter-dropdown {
    width: 100%;
  }

  .side-filter-dropdown {
    width: 50%;
  }
}
</style>
