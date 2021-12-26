<template>
  <div class="c-menu" :class="classes">
    <slot></slot>
  </div>
</template>

<script setup lang="ts">
import {computed, provide, ref, onMounted, onUpdated, ComponentInternalInstance} from "vue";
import {getCurrentInstance} from 'vue'

let props = defineProps({
  selected: {
    type: Array,
    default: () => []
  },
  multiple: {
    type: Boolean,
    default: false
  },
  direction: {
    type: String,
    default: 'horizontal',
    validator: (value: string) => {
      return ['horizontal', 'vertical'].indexOf(value) >= 0
    }
  }
})

provide('root', getCurrentInstance());
provide('direction', props.direction);


let items = ref<ComponentInternalInstance[]>([])
let namePath = ref<any[]>([])
let subMenuItems = ref<ComponentInternalInstance[]>([])
const classes = computed(() => ({
  vertical: props.direction === 'vertical'
}));

let addItem = (vm: ComponentInternalInstance) => {
  items.value.push(vm)
}
let addSubMenuItem = (vm: ComponentInternalInstance) => {
  subMenuItems.value.push(vm)
}
let closeAllPopover = (vm: ComponentInternalInstance) => {
  subMenuItems.value.forEach(vm => {
    vm.close()
  })
}
let updateChildren = (vm: ComponentInternalInstance) => {
  items.value.forEach(vm => {
    vm.active = props.selected.indexOf(vm.name) >= 0
  })
}
let listenToChildren = (vm: ComponentInternalInstance) => {
  // items.value.forEach(vm => {
  //   vm.$on('add:selected', name => {
  //     /* istanbul ignore next */
  //     if (props.multiple) {
  //       let copySelected = JSON.parse(JSON.stringify(props.selected))
  //       copySelected.push(name)
  //       this.$emit('update:selected', copySelected)
  //     } else {
  //       this.$emit('update:selected', [name])
  //     }
  //   })
  // })
}

onMounted(() => {
  const vm = (getCurrentInstance as any)();
  updateChildren(vm)
  listenToChildren(vm)
});

onUpdated(() => {
  const vm = (getCurrentInstance as any)();
  updateChildren(vm)
});


</script>

<style lang="scss" scoped>
@import "../../../style/var";

.c-menu {
  color: #fff;
  display: flex;
  background-color: $grey-color;

  &.vertical {
    flex-direction: column;
    overflow: hidden;
  }
}
</style>