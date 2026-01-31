<template>
    <component
        :is="props.componentType"
        :class="{
            'a-label--disabled': isDisabled,
            'a-label--primary': props.styleType === 'primary',
            'a-label--secondary': props.styleType === 'secondary'
        }"
    >
        <slot />
    </component>
</template>
<script setup lang="ts">
    const props = withDefaults(
        defineProps<{
            isDisabled?: boolean
            componentType?: "h1" | "h2" | "h3" | "h4" | "h5" | "p" | "label"
            styleType?: "primary" | "secondary" | "disabled"
        }>(),
        {
            isDisabled: false,
            componentType: "label",
            styleType: "primary"
        }
    )
</script>
<style scoped lang="scss">
    .label--disabled
    {
        color: rgb(255, 255, 255);
        opacity: 0.3;
    }
    .label--primary
    {
        color: rgb(230, 230, 230);
        font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif
    }
    .label--secondary
    {
        color: rgb(200, 200, 200);
        text-decoration: underline;
        font-family: 'calibri';
    }
</style>