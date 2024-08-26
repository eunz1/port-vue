<script setup>
  import {headerList}  from '../Constants'
</script>
<template>
  <header class="header">
    <div class="header__inner">
      <h1 class="header__logo"></h1>
      <ul class="header__menu">
        <li v-for="(list,key) in headerList" :key="key">
          <a :href=list.url>{{ list.title }}</a>
        </li>
      </ul>
    </div>
  </header>
</template>
<script>
export default {
  
}
</script>
<style lang="scss" scoped>
.header {
  position: fixed;
  left:0;
  right:0;
  &__inner {
    display: flex;;
    justify-content: space-between;
  }
  &__menu {
    display: flex;;
  }
}
</style>