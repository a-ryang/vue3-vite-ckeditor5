<script setup lang="ts">
import BaseEditor from './components/editor/BaseEditor.vue'

const handleEditorUpdate = (value: string) => {
  console.log(value)
}
</script>

<template>
  <main>
    <BaseEditor :model-value="'Hello world!'" @update="handleEditorUpdate"/>
  </main>
</template>

<style scoped></style>
