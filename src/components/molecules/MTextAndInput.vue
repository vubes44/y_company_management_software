<template>
  <div class="m-text-and-input">
    <ALabel :componentType="props.componentType">
      <slot name="label" />
    </ALabel>
    <slot name="input" />
  </div>
</template>
<script setup lang="ts">
import ALabel from "../atoms/ALabel.vue";

const props = withDefaults(
  defineProps<{
    componentType?: string;
    isDisabled?: boolean;
    labelStyleType?: "primary" | "secondary" | "disabled";
  }>(),
  {
    isDisabled: false,
    labelStyleType: "primary",
  },
);
</script>
<style scoped lang="scss"></style>
