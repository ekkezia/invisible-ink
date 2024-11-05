<template>
  <div class="container">
    <div class="text"></div>
  </div>
</template>

<script setup lang="ts">
import { TEXT } from './text';
import { onMounted, watch, defineProps } from 'vue';

const props = defineProps({
  secretText: {
    type: String,
    required: false,
    default: 'i love you full',
  },
});

const addSpansToTextDiv = (text: string) => {
  const container = document.querySelector('.text');
  let tempText = TEXT;
  const cleanSecretText = text.replace(/\s/g, '');

  if (container) {
    container.innerHTML = '';

    for (let i = 0; i < cleanSecretText.length; i++) {
      const index = tempText
        .toLowerCase()
        .indexOf(cleanSecretText[i].toLowerCase());

      if (index !== -1) {
        const textNode = document.createTextNode(tempText.substring(0, index));
        container.appendChild(textNode);

        const span = document.createElement('span');
        span.className = 'secret';
        span.textContent = cleanSecretText[i];
        container.appendChild(span);

        tempText = tempText.substring(index + 1);
      } else {
        const unmatchedText = document.createTextNode(cleanSecretText[i]);
        container.appendChild(unmatchedText);
      }
    }

    if (tempText.length > 0) {
      const remainingTextNode = document.createTextNode(tempText);
      container.appendChild(remainingTextNode);
    }
  }
};

// Watch for changes to the secretText prop
watch(
  () => props.secretText,
  () => {
    addSpansToTextDiv(props.secretText);
  },
);

onMounted(() => {
  addSpansToTextDiv('I love you');
});
</script>

<style>
.container {
  width: 800px;
  max-width: 80vw;
  background: white;
  padding: 4rem;
  transform: rotate(0deg);
  border-radius: 0.1rem;
  box-shadow: 0px 0px 10px grey;
  z-index: 1;
  position: absolute;
  top: 30vh;
  left: 10vw;
}

.container:hover,
.container:focus {
  z-index: 2;
}

.text {
  font-size: 1rem;
  font-weight: 400;
  color: black;
  text-decoration: underline dotted blue;
  font-family: 'Edu AU VIC WA NT Guides', sans-serif;
}

.text::selection {
  background-color: greenyellow;
  color: greenyellow;
}

.secret {
  background-color: white;
  color: black;
  animation-duration: 500ms;
}

.secret::selection {
  background-color: white;
}
</style>
