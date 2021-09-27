<template>
  <div class="home">
    <Header></Header>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import BackSelection from '@/components/back-selection/BackSelection.vue'
import Header from "@/components/home/header/Header.vue";

@Component({
  components: {
    BackSelection,
    Header
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
