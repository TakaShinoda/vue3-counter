<template>
  <TheHeader :text="Math.floor(Math.random() * 10) % 2 === 0 ? 'even' : 'odd'" />
  <div v-if="!validationMessageList.length">{{ count }}</div>
  <div v-else v-for="message in validationMessageList" :key="message">
    {{ message }}
  </div>
  <BaseButton :disabled="hasMaxCount" @onClick="plusOne">+</BaseButton>
  <BaseButton :disabled="hasMinCount" @onClick="minusOne">-</BaseButton>
  <br />
  <!-- <input v-model="inputCount" type="number" /> -->

  <!-- カスタム修飾子 -->
  <NumberInput v-model.numberOnly="inputCount" />
  <BaseButton @onClick="insertCount">insert</BaseButton>
</template>

<script>
import TheHeader from './components/TheHeader.vue'
import BaseButton from './components/BaseButton.vue'
import NumberInput from './components/NumberInput.vue'

export default {
  components: {
    TheHeader,
    BaseButton,
    NumberInput
  },
  data() {
    return {
      count: 0,
      inputCount: 0,
      isEditing: false
    }
  },
  watch: {
    // this.inputCountを監視して変化があればメソッド実行する
    // 前回の計算結果と同じ場合キャッシュするため再レンダリングおこらない
    inputCount(value) {
      // 編集中フラグ
      this.isEditing = true
    }
  },
  // リアクティブな値を追跡
  computed: {
    hasMaxCount() {
      return this.count >= 9999
    },
    hasMinCount() {
      return this.count <= 0
    },
    hasMaxInputCount() {
      return this.inputCount > 9999
    },
    hasMinInputCount() {
      return this.inputCount < 0
    },
    validationMessageList() {
      const validationList = []

      if(this.isEditing) {
        validationList.push('編集中...')
      }

      if(this.hasMaxInputCount) {
        validationList.push('9999以上は入力できません')
      }

      if(this.hasMinInputCount) {
       validationList.push('0以下は入力できません') 
      }

      return validationList
    }
  },
  methods: {
    plusOne() {
      this.count++
    },
    minusOne() {
      this.count--
    },
    insertCount() {
      if(this.hasMaxInputCount || this.hasMinInputCount) return
      // v-modelでemitで受け取った値を使っている
      this.count = this.inputCount
      this.isEditing = false
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
