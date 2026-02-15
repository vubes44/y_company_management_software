<template>
  <AButton
    class="m-icon-button"
    :class="{
      'm-icon-button--disabled': props.isDisabled,
      'm-icon-button--primary': props.styleType === 'primary',
      'm-icon-button--secondary': props.styleType === 'secondary',
    }"
    :disabled="props.isDisabled"
    @click="handleClick"
  >
    <AIcon :name="iconName" />
  </AButton>
</template>
<script setup lang="ts">
import AIcon from "../atoms/AIcon.vue";
import AButton from "../atoms/AButton.vue";

const props = withDefaults(
  defineProps<{
    iconName: string;
    isDisabled?: boolean;
    styleType?: "primary" | "secondary";
  }>(),
  {
    isDisabled: false,
    styleType: "primary",
  },
);

const emit = defineEmits<{
  (e: "click", event: MouseEvent): void;
}>();

const handleClick = (event: MouseEvent) => {
  if (props.isDisabled) return;
  emit("click", event);
};
</script>
<style scoped lang="scss">
.m-icon-button {
  padding: 0.25rem;
  width: 32px;
  height: 32px;
  display: flex;
  align-items: center;
  justify-content: center;

  &--disabled {
    cursor: auto;
    opacity: 0.5;
  }

  &--primary {
    background-color: #007bff;
    color: #fff;

    &:hover:not(&--disabled) {
      background-color: #0069d9;
    }
  }

  &--secondary {
    background-color: #6c757d;
    color: #fff;

    &:hover:not(&--disabled) {
      background-color: #5a6268;
    }
  }
}
</style>
