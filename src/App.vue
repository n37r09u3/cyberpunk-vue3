<script setup lang="ts">
import CButton from "./components/button/src/index.vue";
import CButtonGroup from "./components/button-group/src/index.vue";

</script>

<template>
  <h1>cyberpunk ui for vue3</h1>
  <c-button>Default</c-button>
  <c-button size="small" >Enter</c-button>
  <c-button icon="editor">Edit</c-button>
  <c-button :loading="true">Loading</c-button>
  <c-button disabled>Disabled</c-button>
  <br/>
  <br/>
  <c-button-group>
    <c-button icon="arrow-lift">
      Prev
    </c-button>
    <c-button>
      More
    </c-button>
    <c-button icon="arrow-right" icon-position="right">
      Next
    </c-button>
  </c-button-group>

</template>

<style>
html{
  background-color: black;
  color: white;
}
</style>
