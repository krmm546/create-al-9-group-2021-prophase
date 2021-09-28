<template>
  <div class="home">
    <Header/>
    <Video/>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import BackSelection from '@/components/back-selection/BackSelection.vue'
import Header from "@/components/home/header/Header.vue";
import Video from "@/components/video/Video.vue";

@Component({
  components: {
    BackSelection,
    Header,
    Video
  },
})
export default class Home extends Vue {}
</script>

<style lang="scss" scoped>
.home {
  background-color: black;
  color: white;
}
</style>
