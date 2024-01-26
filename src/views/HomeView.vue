<template>
  <div class="container">
    <div class="box-body">
      <span v-for="item in 500" :key="item" @mouseover="getColor" @mouseout="removeColor"></span>
    </div>
  </div>
</template>
<script setup>
import { ref } from 'vue'
const colors = ref(['#e74c3c', '#8e44ad', '#3498db', '#e67e22', '#2ecc71'])

const getColor = function (el) {
  let random = Math.floor(Math.random() * colors.value.length)
  el.target.style.backgroundColor = colors.value[random]
  el.target.style.boxShadow = `0 0 2px ${colors.value[random]}, 0 0 10px ${colors.value[random]}`
}
const removeColor = function (el) {
  setTimeout(() => {
    el.target.style.backgroundColor = '#1d1d1d'
    el.target.style.boxShadow = '0 0 2px #000'
    el.target.style.transition = '0.9s all'
  }, 600)
}
</script>
<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100vh;
}
.container .box-body {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  max-width: 400px;
}
.container .box-body > span {
  display: block;
  width: 16px;
  height: 16px;
  margin: 2px;
  background-color: rgb(29, 29, 29);
  box-shadow: rgb(0, 0, 0) 0px 0px 2px;
  transition: 0.3s all;
}
</style>
