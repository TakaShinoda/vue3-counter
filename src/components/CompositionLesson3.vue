<template>
    <!-- computed: 監視対象に変化があるたび、引数で受け取ったgetter関数を実行して新しいrefオブジェクトを返す -->
    <h1>composition API 色々試す3</h1>
    <p>{{ count }}</p>
    <p>{{ double }}</p>
    <button @click="increment">increment</button>
</template>

<script>
import { ref, computed } from 'vue'

export default {
    setup() {
        // 監視対象をリアクティブ化
        const count = ref(1)
        const count2 = ref(1)
        
        function increment() {
            count.value++
        }

        // countに変があるたびcount * 2の実行結果を返す
        // 読み取り専用なため上書き不可
        const double = computed(() => {
            return count.value * 2
        })

        const immutable = computed(() => {
            return count2.value * 2
        })

        // getter/setterを持つオブジェクトを渡すと上書き可能になる(set経由で上書き)
        const mutable = computed({
            get: () => {
                return count2
            },
            set: (newValue) => {
                count2.value = newValue.value
            }
        })

        console.log(immutable.value = 0) // reactivity.esm-bundler.js:1102 Write operation failed: computed value is readonly
        console.log(mutable.value = 0) // 0

        return {
            count,
            increment,
            double
        }
    }
}
</script>



