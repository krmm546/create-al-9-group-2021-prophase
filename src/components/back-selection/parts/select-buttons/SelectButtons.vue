<template>
  <div class="select-buttons">
    <SelectButton v-for="route in routes" :key="route" :message="route"></SelectButton>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import SelectButton from "@/components/back-selection/parts/select-buttons/select-button/SelectButton.vue";
@Component({
  components: {
    SelectButton
  }
})
export default class BackSelection extends Vue {
  routes = ['HTML', 'STYLE', 'SCRIPT', 'BACK']
}
</script>

<style lang="scss" scoped>
.select-buttons {
  position: absolute;
  top: 150px;
  right: 0;
  display: flex;
  width: 100px;
  flex-direction: column;
}
</style>
