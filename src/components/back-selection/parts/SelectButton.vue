<template>
  <button class="select-button" @click="onClick">{{ message }}</button>
</template>

<script lang="ts">
import {Component, Emit, Prop, Vue} from 'vue-property-decorator';

@Component
export default class SelectButton extends Vue {
  @Prop({ default: 'ボタン', required: true })
  message!: string

  @Emit('click')
  public onClick(): void {return;}
}
</script>

<style lang="scss" scoped>
.select-button {
  display: block;

  background-color: black;
  color: white;

  font-size: 18px;
  height: 40px;
  width: 100px;
  margin: {
    top: 50px;
  }

  outline: none;

  border: 1px solid white;
  border-radius: 0;

  transform-origin: right top;
  transform: rotate(90deg);
}
</style>
