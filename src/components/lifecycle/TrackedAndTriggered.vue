<template>
    <!-- onRenderTracked: コンポーネントの中でリアクティブな値に変化があるたびに発火、引数にはそのイベント -->
    <!-- onRenderTriggered: コンポーネントの中でリアクティブな値を変化させるイベントが起こるたびに発火、引数には変化を起こした時の値 -->
    <p>onRenderTracked / onRenderTriggered</p>
    <div>
        <div>{{ count }}</div>
        <button @click="increment">increment</button>
    </div>
</template>

<script>
import { onRenderTracked, onRenderTriggered, ref }from 'vue'
export default {
    setup() {
        const count = ref(0)
        const increment = () => count.value++

        onRenderTracked((e) => {
            console.log('tracked', e)
        })

        onRenderTriggered((e) => {
            console.log('trigger', e)
        })

        return {
            count,
            increment
        }
    }
}
</script>