<template>
  <div class="header">
    <span class="title">情報工学科</span>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class Header extends Vue {}
</script>

<style lang="scss" scoped>
.header {
  height: 40px;
  background-color: black;
  position: relative;
  border-bottom: 1px solid white;

  .title {
    position: absolute;
    left: 10px;
    top: 5px;
    font-size: 20px;
    font-family: "Hiragino Mincho ProN",serif;
  }
}
</style>
