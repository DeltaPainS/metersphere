<template>
  <div class="drag-bar" v-left-to-right-drag/>
</template>

<script>
export default {
  name: "MsLeft2RightDragBar"
}
</script>

<style scoped>

.drag-bar {
  height: 100%;
  width: 1px;
  position: absolute;
  right: 0;
  top: 0;
  cursor: w-resize;
  background-color: #E6E6E6;
  border: 0;
}

.drag-bar:hover {
  width: 4px;
  background-color: #783887;
}

</style>
