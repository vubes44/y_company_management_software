<template>
  <a :href="props.href" class="m-link">
    <slot />
  </a>
</template>
<script setup lang="ts">
const props = withDefaults(
  defineProps<{
    href: string;
  }>(),
  {
    href: "#",
  },
);
</script>
