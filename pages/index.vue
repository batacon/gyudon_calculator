<template>
  <div>
    <div v-if="pageName == 'home'" class="home">
      <h1>買い物金額は？</h1>
      <div class="cost-input">
        <input v-model="cost" type="number" />
        <span>万円</span>
      </div>
      <button @click="goToResult">START ▶︎</button>
    </div>
    <div v-if="pageName == 'result'" class="result">
      <div>{{ cost }}万？？</div>
      <div>松屋の牛丼</div>
      <div>{{ gyudonCount }}杯分だよ！！</div>
      <div>{{ gyudonDays }}日食えるわ！！</div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

const matsuyaGyudon = 320

export default Vue.extend({
  data() {
    const cost: number = 0
    const pageName: string = 'home'
    return {
      cost,
      pageName,
    }
  },
  computed: {
    gyudonCount(): number {
      return Math.floor((this.cost * 10000) / matsuyaGyudon)
    },
    gyudonDays(): number {
      return Math.floor(this.gyudonCount / 3)
    },
  },
  methods: {
    goToResult() {
      this.pageName = 'result'
    },
  },
})
</script>

<style>
.home,
.result {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 80vh;
  max-width: 400px;
  margin: 0 auto;
}

.cost-input {
  margin-bottom: 32px;
}

input {
  padding: 8px;
  height: 28px;
  border: 2px solid #01499b;
  background-color: #ea581f;
  font-size: 20px;
  color: #01499b;
  text-align: right;
}

button {
  display: block;
  padding: 12px;
  color: #01499b;
  font-size: 20px;
  font-weight: bold;
  background-color: #ffdd4d;
  border: none;
  letter-spacing: 2px;
}

.result {
  font-size: 40px;
  -webkit-text-stroke: 1px #ffdd4d;
}
</style>
