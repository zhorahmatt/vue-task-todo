<script lang="ts" setup>
import { ref } from 'vue';

const message = ref('Task App');
</script>
<template>
  <main>
    <h1>{{ message }}</h1>
    <form>
      <label for="">
        New Task
        <input name="newTask">
      </label>
    </form>
  </main>
</template>

<style scoped>
main {
  max-width: 800px;
  margin: 1rem auto;
}
</style>