<template>
  <div class="home">
    こんにちは
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import BackSelection from '@/components/back-selection/BackSelection.vue'

@Component({
  components: {
    BackSelection
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
