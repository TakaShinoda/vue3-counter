<template>
    <!-- コンポーネントが依存しているリアクティブな値に変化があった場合その要素は再レンダリングされる -->
    <!-- この時mountedフックまで戻るのではなくbeforUpdateおよびonBeforeUpdateがよばれる -->
    <!-- 1度目のマウント処理ではよばればい -->
    <p>beforeUpdate / onBeforeUpdate</p>
    <div ref="countRef">
        {{ count }}
    </div>

    <!-- update / onUpdate は再レンダリングされた後に実行されるライフサイクル -->
</template>

<script>
import { onBeforeUpdate, onMounted, ref } from 'vue'
export default {
    setup() {
        const count = ref(0)
        const countRef = ref(null)

        onMounted(() => {
            // 1秒(1000)毎にcountをインクリメント
            setInterval(() => {
               count.value++ 
            }, 100000);
        })

        onBeforeUpdate(() => {
            // countの変化による再レンダリングの度に実行される
            // レンダリング前のDOMを参照する
            console.log(countRef.value)
        })

        return {
            count,
            countRef
        }
    },
    beforeUpdate() {
        console.log('beforeUpdate')
    }
}
</script>