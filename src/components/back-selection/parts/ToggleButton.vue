<template>
  <button class="toggle-button" @click="onClick">
    <span :class="{ 'open': isOpen }" v-for="i in 3" :key="i"/>
  </button>
</template>

<script lang="ts">
import {Component, Emit, Prop, Vue} from 'vue-property-decorator';

@Component
export default class ToggleButton extends Vue {
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

  span {
    display: block;
    width: 100%;
    height: 2px;
    background-color: white;
    transition: all 0.3s;

    &:nth-of-type(1) {
      margin-bottom: 10px;
      &.open {
        transform-origin: right;
        transform: rotate(-90deg);
      }
    }

    &:nth-of-type(2) {
      &.open {
        transform: translateY(-12px);
        opacity: 1;
      }
      transform-origin: right;
      transform: rotate(-90deg);
      opacity: 0;
    }

    &:nth-of-type(3).open {
      transform-origin: right;
      transform: rotate(-45deg) translate(3px, -18px);
      width: 140%;
    }
  }
}
</style>
