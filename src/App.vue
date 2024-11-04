<script setup lang="ts">
import { ref } from 'vue';
import Text from './components/Text.vue'
import Input from './components/Input.vue'

const secretMessage = ref('');

const updateText = (message: string) => {
  secretMessage.value = message; 
};
</script>

<template>
  <main>
    <Text :secret-text="secretMessage" />
    <Input @submit="updateText" />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
