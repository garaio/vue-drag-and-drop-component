<script lang="ts">
import DragAndDrop from "./components/DragAndDrop.vue";
import { Component, Vue } from "vue-property-decorator";

@Component({
  components: {
    DragAndDrop
  }
})
export default class App extends Vue {}
</script>

<template>
  <div id="app">
    <DragAndDrop />
  </div>
</template>

<style scoped lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background-color: whitesmoke;
}

#app {
  padding: 15px;
}
</style>
