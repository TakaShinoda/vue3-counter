<template>
    <!-- コンポーネントが破棄される直前に呼び出される -->
    <!-- ページ遷移時やダイヤログを閉じた時などのコンポーネントが破棄される直前にやっておきたい処理を記述 -->
    <p>BeforeUnmount / onBeforeUnmount</p>
    <div>Hello</div>
</template>

<script>
import { onBeforeUnmount } from 'vue'
export default {
    setup() {
        onBeforeUnmount(() => {
            // 自身が非表示になる直前に実行される
            console.log('onBeforeUnmount')
        })
    },
    beforeUnmount() {
        console.log('beforeUnmount')
    }
}
</script>