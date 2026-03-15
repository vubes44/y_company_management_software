<template>
  <div :style="{ margin: props.margin }" class="m-text-and-input">
    <ALabel
      :componentType="props.componentType"
      :styleType="props.labelStyleType"
      :isDisabled
    >
      <slot name="label" />
    </ALabel>
    <slot name="input" />
  </div>
</template>
<script setup lang="ts">
import ALabel from "../atoms/ALabel.vue";

const props = withDefaults(
  defineProps<{
    componentType?: "h1" | "h2" | "h3" | "h4" | "h5" | "p" | "label";
    isDisabled?: boolean;
    labelStyleType?: "apptitle" | "secondary" | "disabled";
    margin?: string;
    layoutStyle?:
      | "horizontal"
      | "vertical"
      | "inline"
      | "stacked"
      | "compact"
      | "spaced"
      | "label-left"
      | "label-top"
      | "responsive";
  }>(),
  {
    isDisabled: false,
    labelStyleType: "apptitle",
    margin: "0",
  },
);
</script>

<style scoped lang="scss">
.m-text-and-input {
  --mti-gap: 12px;
  --mti-label-width: 140px;
  --mti-font-size: 14px;

  display: flex;
  gap: var(--mti-gap);
  align-items: center;
  font-size: var(--mti-font-size);

  ALabel {
    flex: 0 0 auto;
  }
  > *:not(ALabel) {
    flex: 1 1 auto;
  }

  &--horizontal {
    flex-direction: row;
    align-items: center;
  }

  &--vertical {
    flex-direction: column;
    align-items: stretch;

    ALabel {
      margin-bottom: 6px;
    }
    > *:not(ALabel) {
      width: 100%;
    }
  }

  &--inline {
    display: inline-flex;
    flex-direction: row;
    align-items: center;
    gap: 8px;
  }

  &--stacked {
    flex-direction: column;
    align-items: stretch;
    gap: 14px;

    ALabel {
      margin-bottom: 0;
    }
  }

  &--compact {
    --mti-gap: 6px;
    --mti-font-size: 13px;
  }

  &--spaced {
    flex-direction: row;
    justify-content: space-between;
    align-items: center;

    ALabel {
      margin-right: 12px;
    }
  }

  &--label-left {
    flex-direction: row;
    align-items: center;

    ALabel {
      width: var(--mti-label-width);
      flex: 0 0 var(--mti-label-width);
      text-align: left;
    }
    > *:not(ALabel) {
      flex: 1 1 auto;
    }
  }

  &--label-top {
    flex-direction: column;
    align-items: stretch;

    ALabel {
      margin-bottom: 6px;
      width: 100%;
    }
  }

  &--responsive {
    flex-direction: row;
    align-items: center;

    @media (max-width: 600px) {
      flex-direction: column;
      align-items: stretch;

      ALabel {
        margin-bottom: 6px;
      }
    }
  }
}
</style>
