<template>
  <div class="backSection">
    <button class="section-toggle-btn" @click="toggle">
      <span class="top bar"></span>
      <span class="bottom bar"></span>
    </button>
    <div class="select-buttons">
      <button class="select-button">HTML</button>
      <button class="select-button">STYLE</button>
      <button class="select-button">SCRIPT</button>
      <button class="select-button">BACK</button>
    </div>

    <div :class="contentClasses">
      <slot></slot>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class BackSelection extends Vue {
  isOpen = false;
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

  .section-toggle-btn {
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

      &.top {
        margin-bottom: 10px;
      }
    }
  }
  .select-buttons {
    position: absolute;
    top: 150px;
    right: 0;
    display: flex;
    width: 100px;
    flex-direction: column;

    .select-button {
      display: block;

      background-color: black;
      color: white;

      font-size: 18px;
      height: 40px;
      width: 100px;
      margin: {
        top: 50px;
      }

      outline: none;

      border: 1px solid white;
      border-radius: 0;

      transform-origin: right top;
      transform: rotate(90deg);
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
