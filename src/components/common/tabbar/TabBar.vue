<template>
  <div id="tab-bar">
    <slot></slot>
  </div>
</template>
<script>
export default {
  name: "TabBar",
};
</script>
<style scoped>
#tab-bar {
  /* 样式 */
  background-color: #f6f6f6;
  height: 49px;
  border-top: 1px solid #eee;
  

  /* 定位设置 */
  position: fixed;
  left: 0;
  right: 0;
  bottom: 0;

  /* 布局 */
  display: flex;
  text-align: center;
}
</style>
