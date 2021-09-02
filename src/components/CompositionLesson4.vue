<template>
    <!-- watchEffect: 引数で受け取った関数内のリアクティブな値に変化があった際に、その関数を都度実行 -->
    <h1>composition API 色々試す4</h1>
    <button @click="increment">increment</button>
    <button @click="stopHandler">stop</button>
</template>

<script>
import { ref, watchEffect } from 'vue'

export default {
    setup() {
        const count = ref(1)

        function increment() {
            count.value++
        }

        // increment関数が動作するたび現在のカウントが出力される
        // 監視をストップさせるための関数が返される
        const stopHandler = watchEffect(() => console.log(count.value))

        return {
            increment,
            stopHandler,
        }
    }
}
</script>