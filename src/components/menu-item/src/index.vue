<template>
  <div
      class="c-menu-item"
      :class="classes"
      :data-name="name"
      @click="onClick"
  >
    <slot></slot>
  </div>
</template>

<script setup lang="ts">
import {watch, ref, useSlots, PropType, computed, inject, onMounted} from 'vue'
import { getCurrentInstance } from 'vue'
let props = defineProps({
      name: {
      type: String,
      required: true,
    }
})

let active = ref(false)
let direction=inject('direction');
let root:any =inject('root');
const classes = computed(() => ({
        active: active,
         vertical: direction === 'vertical'
}));

let onClick = () => {
  root.namePath = []
  /* istanbul ignore next */
  // this.$parent.updateNamePath && this.$parent.updateNamePath()
  // this.$emit('add:selected', this.name)
  // this.root.closeAllPopover()
}

onMounted(() => {
  const vm = (getCurrentInstance as any)();
  root.addItem(vm)
});
</script>

<style lang="scss" scoped>
@import "../../../style/var";

.c-menu-item {
  padding: 12px 24px;
  cursor: pointer;
  transition: all 0.3s;
  a {
    color: inherit;
    text-decoration: none;
  }
  &.active {
    color: $black-color;
    background-color: $primary-color;
    font-weight: $button-font-weight;
  }
  &:hover:not(.active){
    background-color: $grey-light-color;
  }
}
</style>