<template>
  <div class="video">
    <video src="@/assets/top.mp4" loop autoplay muted playsinline></video>
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
}
</style>
