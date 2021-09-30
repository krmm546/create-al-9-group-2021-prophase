<template>
  <div class="sentence">
    <div class="content">
      <slot></slot>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
@Component
export default class Sentence extends Vue {}
</script>

<style lang="scss" scoped>
.sentence {
  margin: 0;
  width: 100%;
  background-color: gray;
  font-family: "Hiragino Mincho ProN",sans-serif;
  font-size: 20px;
  display: flex;
  padding-top: 20px;
  padding-bottom: 20px;
  justify-content: center;
  .content {
    text-align: center;
    width: 340px;
    line-height: 35px;
  }
}
</style>
