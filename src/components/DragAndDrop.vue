<script lang="ts">
import Board from "./Board.vue";
import Card from "./Card.vue";
import { Component, Vue } from "vue-property-decorator";

@Component({
  components: {
    Board,
    Card
  }
})
export default class App extends Vue {
  private items = [
    { id: 0, title: "Item A", list: 1 },
    { id: 1, title: "Item B", list: 1 },
    { id: 2, title: "Item C", list: 2 }
  ];

  private BoardValueOne = 1;
  private BoardValueTwo = 2;

  private get listOne() {
    return this.items.filter(item => item.list === this.BoardValueOne);
  }

  private get listTwo() {
    return this.items.filter(item => item.list === this.BoardValueTwo);
  }
}
</script>

<template>
  <div class="drag-and-drop-wrapper">
    <Board :items="items" :currentBoardValue="BoardValueOne">
      <template v-slot:dropable-component>
        <Card :itemList="listOne">
          <template v-slot:draggable-component="slotProps">{{ slotProps.item.title }}</template>
        </Card>
      </template>
    </Board>
    <Board :items="items" :currentBoardValue="BoardValueTwo">
      <template v-slot:dropable-component>
        <Card :itemList="listTwo">
          <template v-slot:draggable-component="slotProps">{{ slotProps.item.title }}</template>
        </Card>
      </template>
    </Board>
  </div>
</template>

<style scoped lang="scss">
.drag-and-drop-wrapper {
  display: flex;
  justify-content: space-between;
}
</style>