<script setup lang="ts">
import { PiniaVuePlugin } from 'pinia'
import { reactive, ref } from 'vue'
const email = ref('')
const password = ref('')
const user = reactive({ email: '', password: '' })
function createAccount() {
  console.log(email.value, password.value)
  console.log(user.email, user.email)
}

const square = (v) => v * v
const double = (v) => v * 2
const addOne = (v) => v + 1

function pipe(...args){

  return function (v){
  args.forEach((item,index ) => {
   v = item(v)
  })
  return v
  }


const res = pipe(square, double, addOne)
res(3) // 19; addOne(double(square(3)))
</script>

<template>
  <template v-if="user.email.trim().length <= 0"> EMAIL VAZIO</template>
  <template v-else> EMAIL {{ user.email }}</template>
  <form action="" @submit.prevent="createAccount">
    <input type="text" placeholder="Email" v-model="user.email" />
    <input type="password" placeholder="Password" v-model="user.password" />
    <button type="submit">Create Account</button>
  </form>
</template>

<style scoped lang="css"></style>
