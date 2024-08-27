<template>
  <div class="toolbar">
    <div class="toolbar__inner">
      <span class="circle"></span>
      <span class="circle"></span>
      <span class="circle"></span>
    </div>
  </div>
</template>
<style lang="scss" scoped>
.toolbar {
  position: fixed;
  top:15px;
  left:15px;
  right:15px;
  display: flex;
  align-items: center;
  overflow: hidden;
  border-radius: 10px 10px 0 0;
  box-shadow: -3px -16px 20px 0px rgba(0, 0, 0, 0.15);
  &__inner {
    display: flex;
    align-items: center;
    height: 38px;
    width: 100%;
    padding: 10px;
    background: #e5e3e5;
    box-sizing: border-box;
    // border:1px solid blue;;
  }
  .circle {
    width: 10px;
    height: 10px;
    margin-right:5px;
    border-radius: 50%;
    &:nth-child(1){background: #FF4E4E;}
    &:nth-child(2){background: #FFB92D;}
    &:nth-child(3){background: #00CA3B;}
  }
}
</style>