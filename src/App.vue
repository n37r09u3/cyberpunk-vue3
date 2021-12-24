<script setup lang="ts">
import CButton from "./components/button/src/index.vue";

</script>

<template>
  <c-button>Default</c-button>
  <c-button icon="editor">Edit</c-button>
  <c-button :loading="true">Loading</c-button>
  <c-button disabled>Disabled</c-button>
</template>

<style>
html{
  background-color: black;
}
</style>
