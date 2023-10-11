<template>
  <div class="home">
    <h2>{{  appTitle }}</h2>
    <h3>{{ counterTitle }}</h3>
    <div>
      <button class="btn" @click="decreaseCounter">-</button>
      <span class="counter">{{ counter }}</span>
      <button class="btn" @click="increaseCounter">+</button>
    </div>

    <div class="edit">
      <h4>Edit counter title:</h4>
      <input v-model="counterTitle" type="text">
    </div>

    <h3>{{ counterData.title }}</h3>
    <div>
      <button class="btn" @click="decreaseCounterReactive(2)">--</button>
      <button class="btn" @click="decreaseCounterReactive(1)">-</button>
      <span class="counter">{{ counterData.count }}</span>
      <button class="btn" @click="increaseCounterReactive(1, $event)">+</button>
      <button class="btn" @click="increaseCounterReactive(2)">++</button>
    </div>

    <div class="edit">
      <h4>Edit counter reactive title:</h4>
      <input v-model="counterData.title" type="text">
    </div>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue'

//Ref
const counter = ref(0),
      counterTitle = ref("My Counter")
function decreaseCounter() {
  counter.value--
}
function increaseCounter() {
  counter.value++
}

//Reactive
const counterData = reactive({
  count: 0,
  title: 'My Counter'
})
function decreaseCounterReactive(value) {
  counterData.count -= value
}
function increaseCounterReactive(value, e) {
  console.log(e)
  counterData.count += value
}

const appTitle = "My Amazing App"

</script>

<style>
.home {
  text-align: center;
  padding: 20px;
}

.btn,
.counter {
  font-size: 40px;
  margin: 10px;
}
.edit {
  margin-top: 20px;
  margin-bottom: 50px;
}
</style>
