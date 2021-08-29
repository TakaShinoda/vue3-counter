<template>
    <button @click="handleClick"><slot /></button>
</template>

<script>
export default {
    name: 'BaseButton',
    methods: {
        handleClick() {
            // emit第一引数: イベント名を文字列, 第二引数: 親に渡したい値
            this.$emit('onClick')
        }
    }
}
</script>