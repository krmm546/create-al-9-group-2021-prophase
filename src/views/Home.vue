<template>
  <div class="home">
    <BackSelection></BackSelection>
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
