<template>
  <v-app>
    <v-main>
      <v-container class="pa-4">
        <h1 class="mb-4">Ввод с подсказкой</h1>
        <InputWithHint
          :words="wordList"
          :rules="[v => !!v || 'Поле обязательно для заполнения']"
          label="Введите слово"
        />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import InputWithHint from './components/InputWithHint.vue'

export default {
  name: 'App',
  components: {
    InputWithHint,
  },
  data() {
    return {
      wordList: ['apple', 'apricot', 'banana', 'blueberry', 'blackberry', 'grape', 'grapefruit', 'melon', 'mango'],
    }
  },
}
</script>

<style>
body {
  font-family: 'Roboto', sans-serif;
}
</style>
