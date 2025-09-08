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
  <div class="flex flex-col">
    <div v-if="cookieCounter != 0">
      <h1 class="text-2xl flex justify-center">Cookie generated : {{ cookieCounter }}</h1>
    </div>
    <div v-else>
      <h1 class="text-2xl flex justify-center">Click On The Cookie</h1>
    </div>
    <div class="flex flex-col">
      <div v-if="cookieCounter >= 10">
        <div class="flex justify-center">
          <button
            class="bg-white hover:bg-gray-100 text-gray-800 font-semibold py-2 px-4 border border-gray-400 rounded shadow mt-15"
            @click="autoProduction5"
          >
            5 cookies every 10s (cost 5 cookies)
          </button>
        </div>
      </div>
      <div v-if="cookieCounter >= 20">
        <div class="flex justify-center">
          <button
            class="bg-white hover:bg-gray-100 text-gray-800 font-semibold py-2 px-4 border border-gray-400 rounded shadow mt-5"
            @click="autoProduction10"
          >
            10 cookies every 5s (cost 10 cookies)
          </button>
        </div>
      </div>
      <div v-if="cookieCounter >= 30">
        <div class="flex justify-center">
          <button
            class="bg-white hover:bg-gray-100 text-gray-800 font-semibold py-2 px-4 border border-gray-400 rounded shadow mt-5"
            @click="autoProduction30"
          >
            30 cookies every 3s (cost 30 cookies)
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
const cookieCounter = ref(0)
function incrementCookie() {
  cookieCounter.value += 1
}

function autoProduction5() {
  cookieCounter.value = cookieCounter.value - 5
  setInterval(() => {
    cookieCounter.value += 1
  }, 10000)
}

function autoProduction10() {
  cookieCounter.value = cookieCounter.value - 10
  setInterval(() => {
    cookieCounter.value += 10
  }, 5000)
}

function autoProduction30() {
  cookieCounter.value = cookieCounter.value - 30
  setInterval(() => {
    cookieCounter.value += 30
  }, 3000)
}
</script>
