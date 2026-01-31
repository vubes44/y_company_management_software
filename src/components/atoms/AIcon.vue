<template>
    <svg
        :class="['a-icon', { 'is-spin': spin }]"
        :width="sizeStr"
        :height="sizeStr"
        :style="{ width: sizeStr, height: sizeStr }"
        :fill="color"
        role="img"
        :aria-label="name"
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 24 24"
    >
        <title>{{ name }}</title>
        <use :href="`#icon-${name}`"></use>
    </svg>
</template>
<script setup lang="ts">
import { computed } from 'vue'

const props = withDefaults(defineProps<{
    name: string
    size?: number | string
    color?: string
    spin?: boolean
}>(), {
    size: 16,
    color: 'currentColor',
    spin: false
})

const sizeStr = computed(() => typeof props.size === 'number' ? `${props.size}px` : props.size!)
</script>
<style scoped lang="scss">
.a-icon {
  display: inline-block;
  vertical-align: middle;
}

.a-icon.is-spin {
  animation: aicon-spin 1s linear infinite;
}

@keyframes aicon-spin {
  to { transform: rotate(360deg); }
}
</style>