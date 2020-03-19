<template>
  <div>
    <div class="board">
      <div v-for="(row,indexboard) of board" :key="indexboard">
        <div v-for="(box,indexbox) of row" :key="indexbox">
          <box :value="board[indexboard][indexbox]" v-on:click="makeMove(indexboard,indexbox)" />
        </div>
      </div>
    </div>
    <div>
      <button @click="resetgame()">Reset Game</button>
    </div>
  </div>
</template>

<script>
import box from "@/components/box.vue";
export default {
  components: {
    box
  },
  data() {
    return {
      board: [
        ["", "", ""],
        ["", "", ""],
        ["", "", ""]
      ],
      isxturn: true
    };
  },
  methods: {
    makeMove(boardlocation, boxlocation) {
      console.log("make move is running");
      // if (this.board[boardlocation][boxlocation] !== "") {
      //   return;
      // }
      if (this.isxturn == true) {
        console.log("before setting x");
        this.$set(this.board[boardlocation], boxlocation, "X");
        this.isxturn = !this.isxturn;
      } else {
        console.log("before setting y");
        this.$set(this.board[boardlocation], boxlocation, "O");
        this.isxturn = !this.isxturn;
      }
    },
    resetgame() {
      this.board = [
        ["", "", ""],
        ["", "", ""],
        ["", "", ""]
      ];
      this.isxturn = true;
    }
  }
};
</script>

<style>
.board {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
}
</style>