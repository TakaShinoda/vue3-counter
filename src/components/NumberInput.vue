<template>
    <input :value="modelValue" @input="emitValue" type="number" />
</template>

<script>
export default {
    name: 'NumberInput',
    // 配列で指定する場合は文字列で書く
    // コンポーネントがemitする可能性があるイベント名などを記述できる
    emits: ['update:modelValue'],
    props: {
        modelValue: {
            type: Number,
            default: 0
        },
        modelModifiers: {
            default: () => ({})
        },
    },
    methods: {
        emitValue({target: { value } }) {
            if(this.modelModifiers.numberOnly && value === '') {
                value = 0
            }

            this.$emit('update:modelValue', Number(value))
        }
    }
}
</script>