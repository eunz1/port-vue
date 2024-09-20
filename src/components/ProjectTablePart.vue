<template>
  <section class="table section-unit">
    <ul class="summary">
      <li class="summary__item" v-for="(item,index) in summaryListData" :key="index">
        <!-- <div class="summary-img">
            <img src="" alt="">
        </div> -->
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
        date:"21.5 ~ 21.10",
        name:"웹에이전시 DFY 자사홈페이지 리뉴얼",
        skill:"vue3",
        role:"PA"
      },
      {
        date:"21.1 ~ 21.2",
        name:"더현대서울 홈페이지 구축",
        skill:"HTML, CSS, JQUERY, gulp",
        role:"PA"
      },
      {
        date:"19.5 ~ 19.6",
        name:"현대 모빌리티 ZET 홈페이지 구축",
        skill:"HTML, CSS, JQUERY",
        role:"PA"
      },
      {
        date:"18.10 ~ 19.04",
        name:" 현대호텔 LAHAN 웹사이트 구축",
        skill:"HTML, CSS, JQUERY, gulp",
        role:"PA"
      },
      {
        date:"18.11",
        name:"프리메라 홈페이지 리뉴얼 제안 페이지 제작  ",
        skill:"HTML, CSS, JQUERY",
        role:"PA"
      },
      {
        date:"18.7 ~ 18.8",
        name:"Hokkoku Bank Japan 홈페이지 구축  ",
        skill:"HTML, CSS, JQUERY",
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
  .table { 
    padding: 30px 14px;
    background: #000;
    color:#fff;
  }
  .summary {
    font-weight: 200;
    &__item {
      padding: 10px; 
      border-bottom: 1px solid #767373;
    }
    &-text {
      display: grid;
      grid-template-columns: repeat(12, 1fr);
      align-items: center;
      &__date {
        grid-column: 1 / span 2;
      }
      &__name {
        grid-column: span 7;
      }
      &__role {
        grid-column: span 1;
      }
      &__skill {
        grid-column: span 2;
      }
    }

  }
</style>