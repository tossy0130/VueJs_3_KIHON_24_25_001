<script setup>
import { ref, reactive } from 'vue'

const userName = 'Tossy'
console.log(userName);

// ====== オブジェクト
// ref
const title = ref('Vue JS Start')
let price = ref(10.9)
console.log(price)

// reactive
const instructor = reactive({
  name: 'tossy',
  age: 42,
  sns: {
    twitter: '@tossy',
    youtube: '@to'
  },
  email: ref('tossy@gmail.com')
})
console.log(instructor.age)
console.log(instructor.email)

// rasctove , ref 配列
const items = reactive([ref(1), ref(2), 3])
items.reverse()
console.log(items[0].value)

function increment() {
  price.value += 1
  instructor.age += 1
  console.log(price)
}


// オブジェクトも入れれる start
const info = ref({
  students: 1000,
  rating: 4
})
console.log(info.value.students)
console.log(info.value.rating)
// オブジェクトも入れれる end

</script>

<template>
  <h1>Title: {{ title }}</h1>
  <h2>Price: {{ price - 1 }}</h2>

  <h2>Students: {{ info.students }}</h2>
  <h2>Instructor: {{ instructor.age }}</h2>

  <button @click="increment">ボタン01</button>
</template>

<style>
  h1 {
    color: red;
  }
</style>
