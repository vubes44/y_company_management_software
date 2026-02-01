<template>
    <textarea
        :name="name"
        class="a-textarea"
        :class="{
            'a-textarea--disabled': isDisabled,
            'a-textarea--datafield': styleType === 'datafield',
            'a-textarea--settings': styleType === 'settings',
            'a-textarea--another': styleType === 'another'
        }"
        :disabled="isDisabled"
        :value="modelValue"
        @input="onInput"
    ></textarea>
</template>
<script setup lang="ts">
import { toRef } from 'vue'
const props = withDefaults(
    defineProps<{
        modelValue?: string
        isDisabled?: boolean
        name?: string
        styleType?: "datafield" | "settings" | "another"
    }>(),
    {
        modelValue: '',
        isDisabled: false,
        styleType: 'another'
    }
)
const emit = defineEmits<(e: 'update:modelValue', v: string) => void>()
const modelValue = toRef(props, 'modelValue')
const onInput = (e: Event) => {
    const val = (e.target as HTMLTextAreaElement).value
    emit('update:modelValue', val)
}
</script>
<style scoped lang="scss">
    .a-textarea {
        display: inline-block;
        width: 100%;
        min-height: 100px;
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
        }

        &--datafield {

        }

        &--settings {

        }

        &--another {

        }
    }
</style>