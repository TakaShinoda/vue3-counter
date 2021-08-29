<template>
  <TheHeader :text="Math.floor(Math.random() * 10) % 2 === 0 ? 'even' : 'odd'" />
  <div>{{ count }}</div>
  <BaseButton @onClick="plusOne">+</BaseButton>
  <BaseButton @onClick="minusOne">-</BaseButton>
  <br />
  <input v-model="inputCount" type="number" />
  <BaseButton @onClick="insertCount">insert</BaseButton>
</template>

<script>
import TheHeader from './components/TheHeader.vue'
import BaseButton from './components/BaseButton.vue'

export default {
  components: {
    TheHeader,
    BaseButton
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
