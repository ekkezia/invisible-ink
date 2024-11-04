<script setup lang="ts">
  import { ref, defineEmits } from 'vue';

  const emit = defineEmits();

  const message = ref('');

  const submitMessage = () => {
    emit('submit', message.value); 
    console.log('emitting submit', message.value)
    message.value = ''; 
  };
</script>

<template>
  <div class="container">
    <h3>Your Invisible Ink</h3>
    <input v-model="message" placeholder="Your secret message" />
    <button @click="submitMessage">↵ Enter</button>
  </div>
</template>

<style>
.container {
  background: white;
  padding: 4rem;
  transform: rotate(5deg);
  border-radius: 0.1rem;
  box-shadow: 0px 0px 10px grey;
  z-index: 0;
  position: absolute;
  ::selection {
  background: greenyellow;
  cursor: url("logo.svg"), url("logo.svg"), default;
  }
}

h3 {
  font-weight: 700;
  text-emphasis-style: '₊⊹';
  font-family: 'Edu AU VIC WA NT Guides', sans-serif;
  color: black;
  ::selection {
  color: greenyellow;
  cursor: url("logo.svg"), url("logo.svg"), default;
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
