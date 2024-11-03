<script setup lang="ts">
import Text from './components/Text.vue'
</script>

<template>
  <main>
    <Text />
  </main>
</template>

<style scoped>
main {
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
