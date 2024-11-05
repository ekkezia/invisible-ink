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
    <h3>Your Invisible Ink <span class="highlight"></span></h3>
    <p>
      Type your secret message, press [↵ Enter], then reveal it to your loved
      ones by highlighting the script underneath with your cursor.
    </p>
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
}

h3 {
  font-weight: 700;
  font-size: 2rem;
  text-emphasis-style: '₊⊹';
  font-family: 'Edu AU VIC WA NT Guides', sans-serif;
  color: black;
  background-color: white;
}

h3::selection {
  background-color: greenyellow;
  color: greenyellow;
}

p {
  font-family: Courier;
  font-size: 0.9rem;
  line-height: 1;
  margin: 1rem 0;
  color: grey;
}

input {
  font-size: 1.2rem;
  font-weight: 400;
  color: var(--color-heading);
  color: black;
  text-decoration: underline dotted blue;
  border: none;
  font-family: 'Edu AU VIC WA NT Guides', sans-serif;
}

input::selection {
  background-color: greenyellow;
}

input:focus {
  border: 1px dotted blue;
}

button {
  padding: 1rem;
  font-weight: 700;
  cursor: pointer;
  margin-left: 0.5rem;
  font-family: Courier;
  &:hover {
    background: black;
    color: white;
  }
}

.highlight {
  min-width: 20px;
  height: 2rem;
  background-color: greenyellow;
}
</style>
