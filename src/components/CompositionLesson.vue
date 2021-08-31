<template>
    <h1>composition API 色々試す</h1>
    私は{{ animal.type }}です。
    <button @click="setType('cat')">set</button>
    
    <!-- ref -->
    <p>{{ foo }}</p>

    <div>
        <!-- ref属性にref()で生成した値を渡す -->
        <div ref="countRef">{{ count }}</div>
        <button @click="getCountRef">getCountRef</button>
    </div>
</template>

<script>
import { reactive } from 'vue'
import { ref } from 'vue'
export default {
    // name: 'CompositionLesson'
    setup() {
        // リアクティブ化されたオブジェクト(プロキシ)が返却
        const animal = reactive({
            type: 'Dog'
        })

        // animal.typeを上書きする関数
        function setType(type) {
            animal.type = type
        }

        const foo = ref('foo')
        // 返却値はrefのvalueにアクセスする
        console.log(foo.value)

        const obj = ref({
            bar: 'baz'
        })
        console.log(obj.value.bar) // bar

        const count = ref(0)
        const countRef = ref(null)

        const getCountRef = () => {
            console.log(countRef.value) // <div>0</div>
        } 

        return {
            animal,
            setType,
            foo,
            count,
            countRef,
            getCountRef
        }
    }
}
</script>