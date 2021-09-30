<template>
  <div class="home">
    <Header/>
    <Video/>
    <Sentence>
      奈良高専の情報工学科では、<br>
      JavaScriptやCSSについて学ぶこともできます
    </Sentence>
    <SlideInPicture pictureName="slide-picture-1.png" v-for="i in 20" :key="i" :wait-seconds="i * 0.2"/>
    <span id="last"></span>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import BackSelection from '@/components/back-selection/BackSelection.vue'
import Header from "@/components/home/header/Header.vue";
import Video from "@/components/video/Video.vue";
import Sentence from "@/components/contents/Sentence.vue"
import SlideInPicture from "@/components/contents/SlideInPicture.vue";

@Component({
  components: {
    BackSelection,
    Header,
    Video,
    Sentence,
    SlideInPicture
  },
})
export default class Home extends Vue {
  amountScrollY = 0

  mounted(): void {
    window.onload = () => {
      setInterval(() => {
        this.amountScrollY += 2;
        scrollTo(0, this.amountScrollY)
      }, 1)
    }
  }
}
</script>

<style lang="scss" scoped>
.home {
  background-color: black;
  color: white;
}
.space {
  height: 1000px;
}
</style>
