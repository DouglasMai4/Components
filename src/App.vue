<script setup lang="ts">
</script>

<template>
  <main>
    <section>
      <h1 class="text-primary">Custom Components VUE</h1>
    </section>
  </main>
</template>

<style scoped lang="scss">
  @import './assets/colors.scss';

  main {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100dvh;

    section {
      padding: 1rem;
      border-radius: 10px;
      background-color: $bg-color-s;
      border: 1px solid black;
      box-shadow: 5px 5px 15px rgb(18 18 18 / 50%);
    }
  }
</style>
