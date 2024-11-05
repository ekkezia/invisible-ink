<script setup lang="ts">
import { ref, defineEmits } from 'vue';

const emit = defineEmits();

const message = ref('');

let containerZIndex = ref(1);

const submitMessage = () => {
  emit('submit', message.value);
  // message.value = '';
  containerZIndex.value = 0;
};
</script>

<template>
  <div class="input-container" :style="{ zIndex: containerZIndex }">
    <h3>Your Invisible Ink</h3>
    <input
      v-model="message"
      @keyup.enter="submitMessage"
      placeholder="Your secret message"
    />
    <button @click="submitMessage">↵ Enter</button>
  </div>
</template>

<style>
.input-container {
  width: 800px;
  max-width: 80vw;
  background: white;
  padding: 4rem;
  transform: rotate(5deg);
  border-radius: 0.1rem;
  box-shadow: 0px 0px 10px grey;
  z-index: 0;
  position: absolute;
  top: 10vh;
  left: 10vw;
  ::selection {
    background: greenyellow;
    cursor: url('logo.svg'), url('logo.svg'), default;
  }
}

h3 {
  font-weight: 700;
  font-size: 2rem;
  text-emphasis-style: '₊⊹';
  font-family: 'Edu AU VIC WA NT Guides', sans-serif;
  color: black;
  background-color: white;
  ::selection {
    color: greenyellow;
    cursor: url('logo.svg'), url('logo.svg'), default;
  }
}

input {
  font-size: 1.2rem;
  font-weight: 400;
  color: var(--color-heading);
  color: black;
  text-decoration: underline dotted blue;
  border: none;
}

input:focus {
  border: 1px dotted blue;
}

button {
  padding: 1rem;
  font-weight: 700;
  cursor: pointer;
  margin-left: 0.5rem;
  &:hover {
    background: black;
    color: white;
  }
}
</style>
