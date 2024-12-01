<script setup>
import { ref } from 'vue'

const vueURL = ref('https://vuejs.org')
const vueId = ref('vue-link')

// v-on 用
const count = ref(0)
function countUp() {
  count.value++
}

// event
const count2 = ref(0)
function countUp2(event) {
  // ボタンの X座標取得
  count2.value = event.clientX
}

// event 引数
function countUp3(event, val) {
  count2.value = event.clientX * val
}

// 動的イベント
const eventName = 'keyup'
const countE = ref(0)
</script>

<template>
  <a v-bind="{ id: vueId, href: vueURL }">link</a><br />
  <button>button</button><br />

  <!-- v-on 省略記号 @-->
  <p>{{ count }}</p>
  <button @click="count++">インクリメント</button><br />
  <button v-on:click="countUp">インクリメント関数</button><br />

  <!-- eventハンドラー -->
  <p>X座標 {{ count2 }}</p>
  <button @click="count2 = $event.clientX">インラインハンドラーで X座標取得</button><br />
  <button @click="countUp2">X座標</button><br />

  <!-- eventハンドラー に引数を渡す -->
  <button @click="countUp3($event, 100)">event引数</button><br />

  <!-- event ストップ -->
  <p>{{ count }}</p>
  <div @click="count++">
    <!-- stopPropagation() と .stop は同じ -->
    <button @click="click.stop">click.stop</button><br />
  </div>

  <!-- preventDefault() と .prevent 同じ -->
  <a href="https://vue.js.org" @click.prevent="">click.prevent</a><br />

  <!-- キー 修飾子-->
  <!-- 特定のキーを押して時に実行されるイベント -->
  <input type="text" @keyup.space.delete="count++" /><br />

  <p>{{ countE }}</p>
  <!-- 動的にイベント eventName を選択 -->
  <input type="text" @[eventName].space.delete="countE++" /><br />
</template>
