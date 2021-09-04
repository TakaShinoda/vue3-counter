<template>
<!-- コンポーネントインスタンスがマウントされる(DOMに反映される)直線に呼び出されるメソッド -->
<!-- ライフサイクルフックは接頭辞にonがつく -->
<!-- ライフサイクルメソッド(beforeMount)とライフサイクルフック(onBeforeMount)の同時使用はフックが優先 -->
    <div id="app1">
        <p>beforeMount / onBeforeMount</p>
    </div>
</template>

<script>
import { onBeforeMount } from '@vue/runtime-core'
export default {
    el: '#app1',
    setup() {
        onBeforeMount(() => {
            // beforMountより先に実行される
            console.log('onBeforeMount')
        })
    },
    data() {
        return {
            test: 'test'
        }
    },
    beforeMount() {
        // thisから他のプロパティにアクセスできる
        console.log(this.test)

        // 置き換え対象のDOM要素へアクセスできる最後のタイミング
        console.log(this.$el)
    }
}
</script>