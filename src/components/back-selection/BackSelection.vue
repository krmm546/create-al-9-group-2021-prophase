<template>
  <div class="backSection">

    <ToggleButton @click="toggle" :isOpen="isOpen"></ToggleButton>
    <div class="select-buttons">
      <SelectButton v-for="route in routes" :key="route" :message="route"></SelectButton>
    </div>

    <div :class="contentClasses">
      <slot></slot>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import ToggleButton from './parts/ToggleButton.vue'
import SelectButton from "@/components/back-selection/parts/SelectButton.vue";
@Component({
  components: {
    ToggleButton,
    SelectButton
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


  .select-buttons {
    position: absolute;
    top: 150px;
    right: 0;
    display: flex;
    width: 100px;
    flex-direction: column;
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
