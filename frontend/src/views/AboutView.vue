<script setup lang="ts">
import { ref } from 'vue';
import axios from 'axios';

const email = ref('');
const password = ref('');
 
const doLogin = () => {
  axios.get('/sanctum/csrf-cookie').then(() => {
    axios.post('/login', {
      email: email.value,
      password: password.value,
    })
  });
}
</script>

<template>
  <div class="about">
    <h1>ログイン</h1>
    <form @submit.prevent="doLogin">
      <div>
        <label>Eメール</label>
        <input type="text" v-model="email" />
      </div>
      <div>
        <label>パスワード</label>
        <input type="password" v-model="password" />
      </div>
      <button type="submit">ログイン</button>
    </form>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
