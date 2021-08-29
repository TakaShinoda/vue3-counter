<template>
  <TheHeader :text="Math.floor(Math.random() * 10) % 2 === 0 ? 'even' : 'odd'" />
  <div>{{ count }}</div>
  <BaseButton @onClick="plusOne">+</BaseButton>
  <BaseButton @onClick="minusOne">-</BaseButton>
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
      inputCount: 0
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
      // v-modelでemitで受け取った値を使っている
      this.count = this.inputCount
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
