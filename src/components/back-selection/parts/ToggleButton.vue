<template>
  <button class="toggle-button" @click="onClick">
    <span :class="topBarClasses"></span>
    <span :class="middleBarClasses"></span>
    <span :class="bottomBarClasses"></span>
  </button>
</template>

<script lang="ts">
import {Component, Emit, Prop, Vue} from 'vue-property-decorator';

@Component
export default class ToggleButton extends Vue {
  get topBarClasses(): string[] {
    if (this.isOpen) return ['top', 'bar', 'open']
    return ['top', 'bar']
  }
  get middleBarClasses(): string[] {
    if (this.isOpen) return ['middle', 'bar', 'open']
    return ['middle', 'bar']
  }
  get bottomBarClasses(): string[] {
    if (this.isOpen) return ['bottom', 'bar', 'open']
    return ['bottom', 'bar']
  }
  @Prop({ default: false, required: true })
  isOpen!: boolean

  @Emit('click')
  public onClick(): void {return;}
}
</script>

<style lang="scss" scoped>
.toggle-button {
  position: absolute;
  display: block;
  right: 10px;
  top: 10px;
  width: 40px;
  height: 16px;
  background-color: transparent;
  border: none;
  outline: none;
  z-index: 2;

  .bar {
    display: block;
    width: 100%;
    height: 2px;
    background-color: white;
    transition: all 0.3s;

    &.top {
      margin-bottom: 10px;
      &.open {
        transform-origin: right;
        transform: rotate(-90deg);
      }
    }

    &.middle {
      &.open {
        transform: translateY(-12px);
        opacity: 1;
      }
      transform-origin: right;
      transform: rotate(-90deg);
      opacity: 0;
    }

    &.bottom.open {
      transform-origin: right;
      transform: rotate(-45deg) translate(3px, -18px);
      width: 140%;
    }
  }
}
</style>
