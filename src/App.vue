<script setup lang="ts">
import CButton from "./components/button/src/index.vue";
import CButtonGroup from "./components/button-group/src/index.vue";
import CMenu from "./components/menu/src/index.vue";
import CMenuItem from "./components/menu-item/src/index.vue";

</script>

<template>
  <h2>cyberpunk ui for vue3</h2>
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
  <br/>
  <br/>
<div>
  <c-menu v-model:selected="selectedMenu" :multiple="false">
    <c-menu-item name="home">Home</c-menu-item>
    <c-sub-menu name="about">
      <template slot="title">About</template>
      <c-menu-item name="about1">About1</c-menu-item>
      <c-menu-item name="about2">About2</c-menu-item>
      <c-sub-menu name="contact">
        <template slot="title">Contact</template>
        <c-menu-item name="qq">QQ</c-menu-item>
        <c-menu-item name="phone">Phone</c-menu-item>
        <c-menu-item name="wechat">WeChat</c-menu-item>
      </c-sub-menu>
    </c-sub-menu>
    <c-menu-item name="hire">Hire</c-menu-item>
    <c-menu-item name="google">
      <a href="https://google.com" target="_blank">Google</a>
    </c-menu-item>
  </c-menu>
</div>
</template>

<style>
html{
  background-color: black;
  color: white;
}
h2{
  font-family: BlenderProBold,sans-serif;
  font-size: 56px;
  font-weight: 700;
  letter-spacing: -2px;
  line-height: 1.0714;
  margin: 0 0 18px;
  padding-bottom: 14px;
  position: relative;
  text-transform: uppercase;
}
</style>
