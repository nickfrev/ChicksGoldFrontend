<script setup lang="ts">
import { ref } from 'vue'

const internalValue = ref<string | null>(null)
const internalLabel = ref<string | null>(null)

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
  if (found) {
    internalLabel.value = found.label
  } else {
    internalLabel.value = null
  }
  if (found && found.href) {
    window.location.href = found.href
    target.value = ''
    internalValue.value = null
    internalLabel.value = null
  }
}

if (props.value) {
  internalValue.value = props.value
  internalLabel.value = props.label
} else {
  const defaultOption = props.options.find((cur) => cur.default)
  internalValue.value = defaultOption ? defaultOption.value : null
  internalLabel.value = defaultOption ? defaultOption.label : null
}
</script>

<template>
  <select id="pet-select" @change="changeHandler" v-model="internalValue">
    <button>
      <div class="icon-slot">
        <slot name="icon" />
      </div>
      <span v-if="internalValue !== null && internalValue !== ''">
        <span class="small-title">{{ title }}</span>
        <span class="value-display">{{ internalLabel }}</span>
      </span>
      <span v-else class="large-title">{{ title }}</span>

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
  position: relative;
  background-color: #353a4e;
  border-radius: 0px;

  height: 50px;
  vertical-align: middle;
  line-height: 50px;
  padding-right: 20px;
}

select > button {
  overflow: visible;
}

.icon-slot {
  height: 50px;
  width: 40px;
  text-align: center;
  padding-top: 5px;
}

.small-title {
  display: block;
  font-size: 0.65rem;

  color: rgb(187, 187, 187);
  margin-bottom: -8px;
}

.large-title {
  line-height: 45px;
  font-size: 0.9rem;
  color: white;
}

.value-display {
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
