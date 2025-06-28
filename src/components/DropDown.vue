<script setup lang="ts">
import ChevronUpIcon from 'vue-material-design-icons/ChevronUp.vue'
import { ref } from 'vue'

const internalValue = ref<string | null>(null)

const props = defineProps<{
  title: string
  options: Array<{
    value: string
    label: string
    icon?: string
    default?: boolean
    href?: string
  }>
  value?: string
}>()

function changeHandler(event: Event) {
  const target = event.target as HTMLSelectElement
  const selectedValue = target.value

  internalValue.value = selectedValue

  const found = props.options.find((cur) => cur.value === selectedValue)
  if (found && found.href) {
    window.location.href = found.href
    target.value = ''
    internalValue.value = null
  }
}

if (props.value) {
  internalValue.value = props.value
} else {
  const defaultOption = props.options.find((cur) => cur.default)
  internalValue.value = defaultOption ? defaultOption.value : null
}
</script>

<template>
  <select id="pet-select" @change="changeHandler" v-model="internalValue">
    <button>
      <span v-if="internalValue !== null && internalValue !== ''">{{ internalValue }}</span>
      <span v-else>{{ title }}</span>
      <ChevronUpIcon class="chevron" />

      <!-- <div v-if="internalValue !== null && internalValue !== ''" class="selected-value">
        {{ internalValue }}
      </div> -->
    </button>

    <option v-for="cur in options" :value="cur.value ?? ''" :key="cur.value">
      <div v-if="cur.value">
        <span class="icon" aria-hidden="true" v-if="cur.icon">{{ cur.icon }}</span
        ><span class="option-label">{{ cur.label }}</span>
      </div>
      <div v-else>
        <span class="option-label">Clear</span>
      </div>
    </option>
  </select>
</template>

<style scoped>
select,
::picker(select) {
  appearance: base-select;
}

select {
  color: white;
  border: none;
  font-family: 'Montserrat', sans-serif;
  font-weight: 500;
  font-size: 0.8rem;
  margin: 5px 18px 0px 18px;
  position: relative;
}

select::picker-icon {
  content: '';
}

select > button {
  text-transform: uppercase;

  overflow: visible;
}

.selected-value {
  position: absolute;
  top: 24px;
  left: 18px;
}

.chevron {
  rotate: 180deg;
  margin-top: -10px;
  margin-left: -10px;
}

select:open > .chevron {
  rotate: 0deg;
}

button > span {
  line-height: 25px;
}

option {
  color: white;
  background-color: #37384b;
}

option:hover {
  background-color: #4c6085;
}
</style>
