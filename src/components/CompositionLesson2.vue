<template>
    <!-- readonly: 引数で受け取ったオブジェクトを読み取り専用なリアクティブオブジェクトにして返す -->
    <h1>composition API 色々試す2</h1>
    <p>consoleをみて</p>

</template>

<script>
import { reactive, readonly } from '@vue/reactivity'
export default {
    setup() {
        const state = reactive({
            id: 1,
            name: 'Evan You'
        })

        const readonlyState = readonly(state)

        // Set operation on key "name" failed: target is readonly. 
        console.log(readonlyState.name = '')

        // 元のオブジェクトは変更できる
        console.log(state.name = '')

        // 元のオブジェクトがリアクティブな場合、読み取り専用オブジェクトも影響を受ける
        console.log(readonlyState.name) // ''
    }
}
</script>

