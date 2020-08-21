<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component({
  components: {}
})
export default class App extends Vue {
  @Prop() private items!: [];
  @Prop() private currentBoardValue!: number;

  private onDrop(evt: any, list: any) {
    const itemID = evt.dataTransfer.getData("itemID");
    const item = this.items.find(item => item.id == itemID);
    item.list = list;
  }
}
</script>

<template>
  <div
    class="drop-zone"
    @drop="onDrop($event, currentBoardValue)"
    @dragover.prevent
    @dragenter.prevent
  >
    <slot name="dropable-component" />
  </div>
</template>

<style scoped lang="scss">
.drop-zone {
  background-color: #eee;
  margin-bottom: 10px;
  padding: 10px;
  width: 40%;
  margin: 10px;
}
</style>