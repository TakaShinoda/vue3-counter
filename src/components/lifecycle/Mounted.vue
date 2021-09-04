<template>
    <div id="app2">
        <!-- コンポーネントがDOMへマウントされた時に実行されるライフサイクル -->
        <p>monted / onMounted</p>
    </div>
</template>

<script>
import { nextTick, onMounted } from '@vue/runtime-core'
export default {
    el: '#app2',
    setup() {
        onMounted(() => {
            // mountedより先に実行
            console.log(onMounted)

            nextTick(() => {
                // 子コンポーネントが全てマウントされた後に実行したい処理をかく
            })
        })
    },
    data() {
        return {
            test: 'test'
        }
    },
    mounted() {
        this.$nextTick(() => {
            // Options APIも同様にnextTickで子のマウント後の処理をかく
        })
        console.log(this.$el)
    }
}
</script>
