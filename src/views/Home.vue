<template>
  <div class="home">
    <Header/>
    <Video/>
    <Sentence>
      奈良高専の情報工学科では、<br>
      JavaScriptやCSSについて学ぶこともできます
    </Sentence>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import BackSelection from '@/components/back-selection/BackSelection.vue'
import Header from "@/components/home/header/Header.vue";
import Video from "@/components/video/Video.vue";
import Sentence from "@/components/contents/Sentence.vue"

@Component({
  components: {
    BackSelection,
    Header,
    Video,
    Sentence
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
