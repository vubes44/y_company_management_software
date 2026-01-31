<template>
    <input
        :type="resolvedType"
        :name="props.name"
        class="a-input"
        :class="{
            'a-input--disabled': props.isDisabled,
            'a-input--login': props.styleType === 'login',
            'a-input--datafield': props.styleType === 'datafield',
            'a-input--settings': props.styleType === 'settings',
            'a-input--chat': props.styleType === 'chat',
            'a-input--another': props.styleType === 'another'
        }"
        :placeholder="props.placeholder"
        :disabled="props.isDisabled"
    >
</template>
<script setup lang="ts">
import { computed } from 'vue'

const props = withDefaults(
    defineProps<{
        isDisabled?: boolean
        name?: string
        inputType?: "text" | "password" | "number" | "submit" | "email" | "phone" | "date"
        styleType?: "login" | "datafield" | "settings" | "chat" | "another"
        placeholder?: string
    }>(),
    {
        isDisabled: false,
        inputType: "text",
        styleType: "another",
        placeholder: ""
    }
)
const resolvedType = computed(() => (props.inputType === 'phone' ? 'tel' : props.inputType))
</script>
<style scoped lang="scss">
.a-input {
    display: inline-block;
    width: 100%;
    padding: 0.5rem 0.75rem;
    border: 1px solid #dcdcdc;
    border-radius: 6px;
    font-size: 1rem;
    color: #111;
    background: #fff;
    transition: border-color .15s ease, box-shadow .15s ease;

    &:focus {
        outline: none;
        border-color: #66afe9;
        box-shadow: 0 0 0 3px rgba(102, 175, 233, 0.15);
    }

    &--disabled {
        background: #f5f5f5;
        color: #8a8a8a;
        border-color: rgba(10,10,10,0.08);
        cursor: not-allowed;
        pointer-events: none;
    }

    &--login {
        border-color: #1e88e5;
        background: #f3f9ff;
        color: #0b3d66;
    }

    &--datafield {
        border-color: #e0e0e0;
        background: #fff;
        font-size: 0.95rem;
    }

    &--settings {
        background: #fafafa;
        border-color: #ececec;
        font-size: 0.9rem;
        color: #333;
    }

    &--chat {
        border-radius: 20px;
        padding: 0.5rem 0.9rem;
        background: #fffefc;
        border-color: #ffe9b3;
    }
}
</style>