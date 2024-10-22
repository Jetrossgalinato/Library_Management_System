<script setup>
import { ref } from 'vue'

const theme = ref(localStorage.getItem('theme') ?? 'light')

function onClick() {
  theme.value = theme.value === 'light' ? 'dark' : 'light'
  localStorage.setItem('theme', theme.value)
}
</script>

<template>
  <v-responsive class="border rounded">
    <v-app :theme="theme">
      <v-app-bar
        class="px-2"
        :color="theme === 'light' ? 'light-green-lighten-3' : 'green-darken-1'"
      >
        <v-spacer></v-spacer>

        <!-- Update the button color based on the theme -->
        <v-btn
          :icon="theme === 'light' ? 'mdi-weather-sunny' : 'mdi-weather-night'"
          variant="elevated"
          :style="{ backgroundColor: theme === 'light' ? '#43A047' : '#263238', color: 'white' }"
          slim
          @click="onClick"
        ></v-btn>
      </v-app-bar>

      <v-main>
        <slot name="content"></slot>
      </v-main>

      <v-footer
        class="font-weight-bold"
        :color="theme === 'light' ? 'light-green-lighten-3' : 'green-darken-1'"
        elevation="24"
        app
      >
        Copyright © 2024 - Library Management System | All Rights Reserved
      </v-footer>
    </v-app>
  </v-responsive>
</template>
