<template>
  <BackSelection>
    <router-view></router-view>
  </BackSelection>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import BackSelection from '@/components/back-selection/BackSelection.vue'
import HelloWorld from "@/components/HelloWorld.vue";

@Component({
  components: {
    BackSelection,
    HelloWorld
  },
})
export default class App extends Vue {}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
