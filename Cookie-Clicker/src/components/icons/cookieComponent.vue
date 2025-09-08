<template>
  <div>
    <img
      @click="incrementCookie"
      src="/Users/rithchea/Desktop/Academic Project/Cookie-Clicker/Cookie-Clicker/src/assets/Cookie.jpg"
      alt="cookie"
      width="500"
      height="500"
    />
  </div>
  <div v-if="cookieCounter != 0">
    <h1>Cookie generated : {{ cookieCounter }}</h1>
  </div>
  <div v-else>
    <h1>0 cookie generated, click on the cookie</h1>
  </div>
  <div v-if="cookieCounter > 10">
    <h1>Generate 1 cookie every 10 seconds</h1>
    <button @click="autoProduction">Buy for 10 cookies</button>
  </div>
</template>

<script setup>
import { ref } from 'vue'
const cookieCounter = ref(0)
function incrementCookie() {
  cookieCounter.value += 1
}

function autoProduction() {
  cookieCounter.value = cookieCounter.value - 10
  setInterval(() => {
    cookieCounter.value += 1
  }, 10000)
}
</script>
