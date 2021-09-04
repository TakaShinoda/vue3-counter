<template>
    <!-- watchEffect: 引数で受け取った関数内のリアクティブな値に変化があった際に、その関数を都度実行 -->
    <!-- computedとは異なりrefオブジェクトを返さないが代わりに監視を停止させるための関数を返す -->
    <h1>composition API 色々試す4</h1>
    <button @click="increment">increment</button>
    <button @click="stopHandler">stop</button>
</template>

<script>
import { ref, watch, watchEffect } from 'vue'

export default {
    setup() {
        const count = ref(1)

        function increment() {
            count.value++
        }

        // increment関数が動作するたび現在のカウントが出力される
        // 監視をストップさせるための関数が返される
        const stopHandler = watchEffect(() => console.log(count.value))

        // watchはoptions APIと同じ
        const state = ref('0')

        // 監視する値と変更があった際に実行する関数を受け取る
        watch(state, (next, prev) => {
            if(typeof prev === 'string' && typeof next === 'number') {
                console.log('move string => number')
            }
        })

        return {
            increment,
            stopHandler,
        }
    }
}
</script>