<template>
  <select
    :name="name"
    class="a-select"
    :class="{
      'a-select--disabled': isDisabled,
      'a-select--datafield': styleType === 'datafield',
      'a-select--settings': styleType === 'settings',
      'a-select--another': styleType === 'another'
    }"
    :disabled="isDisabled"
    :value="modelValue"
    @change="onChange"
  >
    <option v-if="placeholder" disabled value="">{{ placeholder }}</option>
    <option
      v-for="opt in options"
      :key="opt.value"
      :value="opt.value"
      :disabled="opt.disabled"
    >
      {{ opt.label }}
    </option>
  </select>
</template>

<script setup lang="ts">
import { toRef } from 'vue'

const props = withDefaults(
  defineProps<{
    modelValue?: string | number | null
    options?: { value: string | number; label: string; disabled?: boolean }[]
    isDisabled?: boolean
    name?: string
    styleType?: "datafield" | "settings" | "another"
    placeholder?: string
  }>(),
  {
    modelValue: null,
    options: () => [],
    isDisabled: false,
    styleType: 'another',
    placeholder: ''
  }
)

const emit = defineEmits<(e: 'update:modelValue', v: string | number | null) => void>()
const modelValue = toRef(props, 'modelValue')

const onChange = (e: Event) => {
  const val = (e.target as HTMLSelectElement).value
  emit('update:modelValue', val === '' ? null : val)
}
</script>

<style scoped lang="scss">
.a-select {
  appearance: none;
  background-image: linear-gradient(45deg, transparent 50%, #111 50%),
                    linear-gradient(135deg, #111 50%, transparent 50%);
  background-position: calc(100% - 1rem) calc(1rem + 2px), calc(100% - .7rem) calc(1rem + 2px);
  background-size: 6px 6px, 6px 6px;
  background-repeat: no-repeat;
  padding-right: 2.25rem;

  &--disabled
  {

  }
  &--datafield
  {

  }
  &--settings
  {

  }
  &--another
  {

  }
}
</style>