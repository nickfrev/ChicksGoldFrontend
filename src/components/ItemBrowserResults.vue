<script setup lang="ts">
import ItemBrowserCard from './ItemBrowserCard.vue'
import IconDropDown from './IconDropDown.vue'
import ChevronRightIcon from 'vue-material-design-icons/ChevronRight.vue'
import ChevronLeftIcon from 'vue-material-design-icons/ChevronLeft.vue'
import TuneIcon from 'vue-material-design-icons/Tune.vue'
import { ref, computed } from 'vue'
const currentPage = ref(0)
const maxDisplayedPages = 9

const props = defineProps<{
  showAmount: integer
  items: Array<{
    id: string
    isOnSale: boolean
    quantity: number
    name: string
    description: string
    price: number
    salePrice?: number
    gameLogo: string
    imageUrl: string
  }>
}>()

const pageArray = computed(() => {
  const maxPages = Math.ceil(props.items.length / props.showAmount)

  if (maxPages <= maxDisplayedPages) {
    return Array.from({ length: maxPages }, (_, i) => i + 1)
  }

  const halfDistance = Math.floor(maxDisplayedPages / 2)
  const hasSkipOnLeft = currentPage.value > halfDistance
  const hasSkipOnRight = currentPage.value < maxPages - 1 - halfDistance

  // Add the first page and a skip if needed
  const returnPages = [1]
  if (hasSkipOnLeft) {
    returnPages.push('...')
  }

  // calculate the range of pages to display in the middle
  let lowerBound = 1
  let upperBound = maxPages - 1
  if (hasSkipOnLeft && hasSkipOnRight) {
    lowerBound = currentPage.value - halfDistance + 2
    upperBound = currentPage.value + halfDistance - 1
  } else if (hasSkipOnLeft) {
    lowerBound = maxPages - maxDisplayedPages + 2
  } else {
    upperBound = maxDisplayedPages - 2
  }
  for (let i = lowerBound; i < upperBound; i++) {
    returnPages.push(i + 1)
  }

  // Add the last page and a skip if needed
  if (hasSkipOnRight) {
    returnPages.push('...')
  }
  returnPages.push(maxPages)

  return returnPages
})
</script>

<template>
  <div class="contents">
    <div class="showing-count">Showing {{ showAmount }} - from {{ items.length }}</div>
    <div class="filter-picklist">
      <IconDropDown
        class="filter-dropdown"
        title="Sort By"
        :options="[
          { value: 'featured', label: 'Featured', default: true },
          { value: 'onsale', label: 'On Sale' },
          { value: 'chickpick', label: 'Chicks Gold Pick', icon: '🐥' },
        ]"
      >
        <template v-slot:icon>
          <TuneIcon class="tune-icon" />
        </template>
      </IconDropDown>
    </div>
    <div class="item-browser">
      <ItemBrowserCard
        v-for="item in items.slice(
          currentPage * props.showAmount,
          currentPage * props.showAmount + props.showAmount,
        )"
        :item="item"
        :key="item.id"
      />
    </div>
    <div class="page-controls">
      <button
        class="page-button direction-button"
        :disabled="currentPage <= 0"
        @click="currentPage--"
      >
        <ChevronLeftIcon />
      </button>
      <button
        v-for="page in pageArray"
        :key="page"
        class="page-button"
        :class="{ 'current-page': currentPage === page - 1 }"
        :disabled="page === '...' || currentPage === page - 1"
        @click="currentPage = page - 1"
      >
        {{ page }}
      </button>
      <button
        class="page-button direction-button"
        :disabled="(currentPage + 1) * props.showAmount >= items.length"
        @click="currentPage++"
      >
        <ChevronRightIcon />
      </button>
    </div>
  </div>
</template>

<style scoped>
.contents {
  position: relative;
  width: 100%;
  background-color: #303141;
  border: 1px solid #4c6085;
  padding: 50px;
  margin: 10px 0px;
  box-shadow: 0px 0px 15px rgba(0, 0, 0, 0.25);
}

.showing-count {
  font-size: 0.8rem;
  color: #cdcdd1;
  height: 50px;
  line-height: 50px;
  vertical-align: middle;
  margin-bottom: 35px;
}

.filter-picklist {
  position: absolute;
  right: 50px;
  top: 50px;
}

.item-browser {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-content: flex-start;
  gap: 20px;
}

.page-controls {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 50px;
}

.page-button {
  border: none;
  background-color: transparent;
  border-radius: 5px;
  height: 40px;
  width: 40px;
  color: white;
  cursor: pointer;
  margin: 0 3px;

  transition: opacity 0.3s ease;
}

.page-button:disabled {
  cursor: auto;
}

.page-button:disabled:hover {
  border: none;
}

.page-button:hover {
  border: 1px solid #5762d5;
}

.page-button.current-page {
  background-color: #5762d5;
}

.page-button.direction-button {
  border: 1px solid #5762d5;
  margin: 0 10px;
}

.page-button.direction-button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}

.tune-icon {
  color: #39e29d;
}

.filter-dropdown {
  width: 180px;
}
</style>
