<script setup lang="ts">
import { TEXT } from './text';
import { SECRET_TEXT } from './text';
import { onMounted } from 'vue';

const addSpansToTextDiv = () => {
  const container = document.querySelector('.text');
  let tempText = TEXT;
  const cleanSecretText = SECRET_TEXT.replace(/\s/g, "");

  if (container) {
    container.innerHTML = "";

    for (let i = 0; i < cleanSecretText.length; i++) {
      const index = tempText.toLowerCase().indexOf(cleanSecretText[i].toLowerCase());

      if (i == cleanSecretText.length - 1) {
        const textNode = document.createTextNode(tempText);
        container.appendChild(textNode);
      } else {
      if (index !== -1) {
        const textNode = document.createTextNode(tempText.substring(0, index));
        container.appendChild(textNode);

        const span = document.createElement("span");
        span.className = "secret";
        span.textContent = cleanSecretText[i];
        container.appendChild(span);

        tempText = tempText.substring(index + 1);
      } else {
        const unmatchedText = document.createTextNode(cleanSecretText[i]);
        container.appendChild(unmatchedText);
      }
    }
}
  }
};

onMounted(addSpansToTextDiv);
</script>

<template>
  <div class="text"></div>
</template>

<style>
.text {
  font-size: 1.2rem;
  font-weight: 400;
  color: var(--color-heading);
  color: black;
  text-decoration: underline dotted blue;
}

.secret {
  background-color: white;
  color: black;
  animation-duration: 500ms;
}
</style>
