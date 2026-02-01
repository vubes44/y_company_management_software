<template>
    <input
        type="checkbox"
        :class="{
            'a-checkbox--disabled': isDisabled,
            'a-checkbox--primary': styleType === 'primary',
            'a-checkbox--secondary': styleType === 'secondary'
        }"
        :disabled="isDisabled"
        :checked="modelValue"
        @change="onChange"
    />
</template>
<script setup lang="ts">
    import { computed } from 'vue'
    const props = withDefaults(
        defineProps<{
            modelValue?: boolean
            isDisabled?: boolean
            styleType?: "primary" | "secondary"
        }>(),
        {
            modelValue: false,
            isDisabled: false,
            styleType: 'primary'
        }
    )

    const emit = defineEmits<(e: 'update:modelValue', v: boolean) => void>()
    const modelValue = computed<boolean>({
        get: () => props.modelValue as boolean,
        set: (val: boolean) => emit('update:modelValue', val)
    })

    const onChange = (e: Event) => {
        const val = (e.target as HTMLInputElement).checked
        emit('update:modelValue', val)
    }
</script>
<style scoped lang="scss">
    .a-checkbox {
        width: 16px;
        height: 16px;
        border: 1px solid #dcdcdc;
        border-radius: 4px;
        cursor: pointer;
        transition: border-color .15s ease, background-color .15s ease;

        &:checked {
            background-color: #66afe9;
            border-color: #66afe9;
        }

        &--disabled {
            background: #f5f5f5;
            border-color: rgba(10,10,10,0.08);
            cursor: not-allowed;
        }

        &--primary {
            &:checked {
                background-color: #007bff;
                border-color: #007bff;
            }
        }

        &--secondary {
            &:checked {
                background-color: #6c757d;
                border-color: #6c757d;
            }
        }
    }
</style>