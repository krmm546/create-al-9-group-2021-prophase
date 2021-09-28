<template>
  <div class="video">
    <video src="@/assets/top.mp4" loop autoplay muted playsinline></video>
    <span class="title-sentence">Hello World</span>
    <span class="sub-title-sentence">情報の世界へようこそ</span>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
@Component
export default class Video extends Vue {}
</script>

<style lang="scss" scoped>
.video {
  width: 100%;
  overflow: hidden;
  video {
    height: 500px;
  }
  .title-sentence {
    position: absolute;
    color: white;
    font-size: 50px;
    font-family: 'Karma', serif;
    z-index: 3;
    top: 400px;
    left: 10px;
    transform: translateY(-50%);
  }
  .sub-title-sentence {
    position: absolute;
    color: white;
    font-size: 34px;
    font-family: 'Karma', serif;
    z-index: 3;
    top: 450px;
    left: 10px;
  }
}
</style>
