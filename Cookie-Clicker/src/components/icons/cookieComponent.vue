<template>
  <div class="flex flex-row justify-center mt-40">
    <div class="flex flex-col items-center">
      <h1 class="text-4xl text-amber-900">Cookie Clicker</h1>
      <img
        @click="incrementCookie"
        src="/Users/rithchea/Desktop/Academic Project/Cookie-Clicker/Cookie-Clicker/src/assets/Cookie.jpg"
        width="450"
        height="450"
        alt="cookie"
      />
      <h1 class="text-2xl" v-if="gameStart === false">Click on the cookie to play !</h1>
      <h1 class="text-2xl" v-if="gameStart === true">
        You produced {{ cookieCounter }} cookie<span v-if="cookieCounter >= 2">s</span>
      </h1>
    </div>
    <div class="flex flex-col gap-1.5">
      <button
        class="bg-white hover:bg-gray-100 text-gray-800 font-semibold py-2 px-4 border border-gray-400 rounded shadow"
        @click="upgrade1Cookie"
        v-if="cookieCounter >= 10"
      >
        Upgrade +1/2s (Cost 10 Cookies)
      </button>
      <button
        class="bg-white hover:bg-gray-100 text-gray-800 font-semibold py-2 px-4 border border-gray-400 rounded shadow"
        @click="upgrade2Cookie"
        v-if="cookieCounter >= 30"
      >
        Upgrade +3/2s (Cost 30 Cookies)
      </button>
      <button
        class="bg-white hover:bg-gray-100 text-gray-800 font-semibold py-2 px-4 border border-gray-400 rounded shadow"
        @click="upgrade3Cookie"
        v-if="cookieCounter >= 75"
      >
        Upgrade +10/2s (Cost 75 Cookies)
      </button>
      <div>
        <h1 class="text-2xl text-orange-700" v-if="cookieCounter >= 50">
          Congratulations for your 50 produced cookies !
        </h1>
        <h1 class="text-2xl text-orange-700" v-if="cookieCounter >= 100">
          Congratulations for your 100 produced cookies !
        </h1>
        <h1 class="text-2xl text-orange-700" v-if="cookieCounter >= 150">
          Congratulations for your 150 produced cookies !
        </h1>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, watch, onMounted } from 'vue'
const gameStart = ref(false)
const cookieCounter = ref(0)

onMounted(() => {
  const savedCookies = localStorage.getItem('cookieCounter')
  if (savedCookies !== null) {
    cookieCounter.value = parseInt(savedCookies)
  }
})

watch(cookieCounter, (newVal) => {
  localStorage.setItem('cookieCounter', newVal)
})

const incrementCookie = () => {
  gameStart.value = true
  cookieCounter.value += 1
}
const upgrade1Cookie = () => {
  cookieCounter.value -= 10
  setInterval(() => {
    cookieCounter.value += 1
  }, 2000)
}
const upgrade2Cookie = () => {
  cookieCounter.value -= 30
  setInterval(() => {
    cookieCounter.value += 3
  }, 2000)
}
const upgrade3Cookie = () => {
  cookieCounter.value -= 75
  setInterval(() => {
    cookieCounter.value += 10
  }, 2000)
}
</script>
