<template>
  <div class="cell" @click="handleClick()">
    <div>{{value}}</div>
  </div>
</template>

<script>
export default {
  props: {
    value: String
  },
  methods: {
    handleClick() {
      console.log("box clicked");
      this.$emit("click");
    }
  }
};
</script>

<style>
.cell {
  height: 80px;
  width: 80px;
  border: 4px solid;
  font-size: 50px;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>