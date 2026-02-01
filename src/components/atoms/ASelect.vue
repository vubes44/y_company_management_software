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
    border: 1px solid #d9dbe0;
    border-radius: 4px;
    padding: 0.45rem 0.75rem;
    font-size: 0.95rem;
    color: #111;
    background-color: #fff;
    transition: border-color 120ms ease, box-shadow 120ms ease;

    &--disabled {
      background-color: #f5f6f8;
      color: #9aa0a6;
      border-color: #e7e8eb;
      cursor: not-allowed;
      opacity: 0.9;
      pointer-events: none;
      background-image: linear-gradient(45deg, transparent 50%, #9aa0a6 50%),
                        linear-gradient(135deg, #9aa0a6 50%, transparent 50%);
    }

    &--datafield {
      padding: 0.35rem 0.6rem;
      font-size: 0.9rem;
      border-radius: 3px;
      border-color: #cfcfcf;
      background-color: #ffffff;
      box-shadow: none;
    }

    &--settings {
      padding: 0.4rem 0.7rem;
      font-size: 0.88rem;
      border-radius: 6px;
      border-color: #e3e6ea;
      background-color: #fbfcfd;
      color: #24303a;
    }

    &--another {
      padding: 0.5rem 0.85rem;
      font-size: 1rem;
      border-radius: 8px;
      border-color: #bcd7fb;
      background-color: #f3f8ff;
      color: #0b5fff;
      font-weight: 500;
    }
  }
</style>