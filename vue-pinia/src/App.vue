
<script setup>
import { ref } from 'vue'
import { RouterView } from 'vue-router'

import { storeToRefs } from 'pinia';
import { useUserStore } from './stores/user.js';


const { theme, user } = storeToRefs(useUserStore())
const { toggleTheme, login,logout } = useUserStore();
</script>


<template>
  <v-app :theme="theme">
    <v-app-bar>
      <v-btn href="/">
        <v-app-bar-title>Logo</v-app-bar-title>
      </v-btn>
      <v-spacer></v-spacer>
      <v-btn href="/">Home</v-btn>
      <v-btn href="/about">about</v-btn>
      <v-btn :icon="theme === 'light' ? 'mdi-weather-sunny' : 'mdi-weather-night'" @click="toggleTheme" />
      <v-btn v-if ="!user" icon="mdi-login" @click="login(1)" />
      <v-btn icon v-if ="user">
        <v-avatar>
          <v-img :src="user.avatar" />
        </v-avatar>
      </v-btn>
      <v-btn v-if ="user" icon="mdi-logout" @click="logout()" />
    </v-app-bar>

    <RouterView />
  </v-app>
</template>




<style scoped>

</style>
