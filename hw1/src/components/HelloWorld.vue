<script setup>
import { ref } from 'vue'

defineProps({
  msg: String,
})

const eggCount = ref(0)
const steakCount = ref(0)
const milksCount = ref(0)




const addEgg = ()=>{
  eggCount.value+=1
}

const addSteak = ()=>{
  steakCount.value +=1
}

const addMilks = ()=>{
  milksCount.value +=1
}

const minusEgg = ()=>{
  if (eggCount.value >0) eggCount.value -=1
}

const minusSteak = ()=>{
  if(steakCount.value >0) steakCount.value-=1
}

const minusMilk = ()=>{
  if(milksCount.value >0) milksCount.value-=1
}

</script>

<template>
  <h1>{{ msg }}</h1>

  <div class="card">
    <button type="button" @click="addEgg">+</button>
    <span>Eggs: {{eggCount}}</span>
    <button type="button" @click.stop="minusEgg">-</button>
  </div>

  <div>
    <button type="button" @click="addSteak">+</button>
    <span>Steak: {{steakCount}}</span>
    <button type="button" @click.stop="minusSteak">-</button>
  </div>

  <div>
    <button type="button" @click="addMilks">+</button>
    <span>Milks: {{milksCount}}</span>
    <button type="button" @click.stop="minusMilks">-</button>
  </div>

  <p>
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank"
      >create-vue</a
    >, the official Vue + Vite starter
  </p>
  <p>
    Learn more about IDE Support for Vue in the
    <a
      href="https://vuejs.org/guide/scaling-up/tooling.html#ide-support"
      target="_blank"
      >Vue Docs Scaling up Guide</a
    >.
  </p>
  <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
