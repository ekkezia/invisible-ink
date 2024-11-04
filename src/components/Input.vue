<script setup lang="ts">

</script>

<template>
  <div class="container">
    <input placeholder="Your secret message" />
  </div>
</template>

<style>
.container {
  background: white;
  padding: 4rem;
  transform: rotate(5deg);
  border-radius: 0.1rem;
  box-shadow: 0px 0px 10px grey;
  ::selection {
  background: greenyellow;
  cursor: url("logo.svg"), url("logo.svg"), default;
  }
}

.input {
  font-size: 1.2rem;
  font-weight: 400;
  color: var(--color-heading);
  color: black;
  text-decoration: underline dotted blue;
}

</style>
