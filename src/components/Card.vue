<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component({
  components: {}
})
export default class App extends Vue {
  @Prop() private itemList!: [];

  private startDrag(evt: any, item: any) {
    evt.dataTransfer.dropEffect = "move";
    evt.dataTransfer.effectAllowed = "move";
    evt.dataTransfer.setData("itemID", item.id);
  }
}
</script>

<template>
  <div>
    <div
      class="drag-el"
      v-for="item in itemList"
      :key="item.title"
      draggable
      @dragstart="startDrag($event, item)"
    >
      <slot name="draggable-component" :item="item"></slot>
    </div>
  </div>
</template>

<style scoped lang="scss">
.drag-el {
  background-color: #fff;
  margin-bottom: 10px;
  padding: 5px;
}
</style>