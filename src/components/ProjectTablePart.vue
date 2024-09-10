<template>
  <section class="table section-unit">
    <ul class="summary">
      <li class="summary__item" v-for="(item,index) in summaryListData" :key="index">
        <div class="summary-img">
            <img src="" alt="">
        </div>
        <div class="summary-text">
          <span class="summary-text__date">{{item.date}}</span>
          <span class="summary-text__name">{{item.name}}</span>
          <span class="summary-text__skill">{{item.skill}}</span>
          <span class="summary-text__role">{{item.role}}</span>
        </div>
      </li>
    </ul>
  </section>
</template>
<script>
import { ref, onMounted, nextTick } from 'vue';
import { gsap } from 'gsap';
import ScrollTrigger from 'gsap/ScrollTrigger';
gsap.registerPlugin(ScrollTrigger);
export default {
  setup() {
    const summaryListData = ref([
      {
        date:"21.1",
        name:"더현대서울",
        skill:"",
        role:"PA"
      },
      {
        date:"21.5",
        name:"DFY리뉴얼",
        skill:"vue3",
        role:"PA"
      }
    ])
    return {
      summaryListData
    }
  }
}
</script>
<style lang="scss" scoped>
</style>