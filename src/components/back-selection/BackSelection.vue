<template>
  <div class="backSection">
    <ToggleButton @click="toggle" :isOpen="isOpen"></ToggleButton>
    <SelectButtons/>
    <div :class="contentClasses">
      <slot></slot>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import ToggleButton from './parts/ToggleButton.vue'
import SelectButtons from "@/components/back-selection/parts/select-buttons/SelectButtons.vue"
@Component({
  components: {
    ToggleButton,
    SelectButtons
  }
})
export default class BackSelection extends Vue {
  isOpen = false
  routes = ['HTML', 'STYLE', 'SCRIPT', 'BACK']

  get contentClasses(): string[] {
    if (this.isOpen) return ['content', 'open']
    return ['content']
  }

  toggle(): void {
    this.isOpen = !this.isOpen
  }
}
</script>

<style lang="scss" scoped>

.backSection {
  position: relative;
  width: 100%;
  height: 100%;

  .content {
    z-index: 1;
    position: absolute;
    height: 100%;
    right: 0;
    top: 0;
    left: 0;
    bottom: 0;
    transition: all 0.3s;

    &.open {
      transform: translate(-45px, 45px);
    }
  }



}
</style>
<style lang="scss">
$cBackSelection: #a29b9b;
html, body {
  background-color: $cBackSelection;
  padding: 0;
  margin: 0;
}
</style>
