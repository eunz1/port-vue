<template>
  <section ref="targetParent" class="project section-unit">
    <!-- <h2 class="project__tit" :class="{'fixed':isFixed}">Project</h2> -->
    <ul ref="target">
      <li class="project__item" v-for="(item, index) in portListData" :key="index" :style="{backgroundColor: item.color}">
        <strong class="project__num lobster">( No.{{ index + 1 }} )</strong>
          <a :href="item.url" target="_blank" class="project__link">
            <figure class="project__logo">
              <img :src="item.img" alt="">
            </figure>
            <div class="project__txt">
              <dl>
                <dt>프로젝트명</dt>
                <dd>{{item.name}}</dd>
              </dl>
              <dl>
                <dt>담당역할</dt>
                <dd>{{item.role}}</dd>
              </dl>
              <dl>
                <dt>업무기간</dt>
                <dd>{{item.duration}}</dd>
              </dl>
              <dl>
                <dt>기술스택</dt>
                <dd>{{item.stack}}</dd>
              </dl>
              <span>
                
              </span>
              <span>

              </span>
            </div>
            <div class="project__go lobster">
             ( <span>View Detail </span>  )
            </div>
          </a>
      </li>
    </ul>
  </section>
</template>
<script>
import { ref, onMounted, nextTick } from 'vue';
import { gsap } from 'gsap';
import ScrollTrigger from 'gsap/ScrollTrigger';
gsap.registerPlugin(ScrollTrigger);

import logo1 from "../assets/Images/company-logo_ok.png"
import logo2 from "../assets/Images/company-logo_max.png"
import logo3 from "../assets/Images/company-logo_samsung.png"
import logo4 from "../assets/Images/company-logo_lotte.png"

export default {
  setup() {
    const target = ref(null)
    const targetParent = ref(null)
    const isFixed = ref(false)
    const portListData = ref([
      {
        name:'명품판매 이커머스 오케이몰 운영',
        role:'PL/PA',
        duration:'2022.01 ~ 2024.04 (2년 4개월)',
        stack:'HTML,CSS,JQUERY',
        img:logo1,
        url:'https://harmonious-fang-850.notion.site/4d816ff6bc46455a8fffcabacadb9465',
        text:'1',
        color:"#000"
      },
      { name:'MPX GALLERY 구축',
        role:'PA',
        duration:'2021.10 ~ 2021.12',
        stack:'HTML, SCSS ,JavaScript, gulp, tailwind',
        img:logo2,
        url:'https://harmonious-fang-850.notion.site/MPX-GALLERY-140fa891ed5d474e95893202abac2731',
        text:'2',
        color:"#003da6"
      },
      { name:'삼성 디지털프라자 프로젝트 구축',
        role:'PA',
        duration:'2021.8 ~ 2021.10',
        stack:'HTML, SCSS ,JavaScript, Gulp',
        img:logo3,
        url:'https://harmonious-fang-850.notion.site/09daae6abc8c4caea5bc721c03186071',
        text:'3',
        color:"#222"
      },
      { name:' 롯데 통합 e커머스 구축 및 운영',
        role:'PA',
        duration:'2019.07~ 2020.12 (1년 6개월)',
        stack:'Vue2, SCSS, JavaScript',
        img:logo4,
        url:'https://harmonious-fang-850.notion.site/LOTTE-ON-19e438e7fa574faabb9c918cc373bfa4',
        text:'4',
        color:"#E4002B"
      }
      
    ])
    
    onMounted(()=>{
      nextTick(()=>{
        const main = document.querySelector('main')
        const targetChild = target.value;
        gsap.to(target.value,{
          scrollTrigger:{
            trigger:target.value,
            start:"top top",
            end:"bottom bottom",
            // markers:true,
            onEnter:()=>{
              console.log('en')
              isFixed.value =true
            },
            onEnterBack:()=>{
              isFixed.value =false
            }
          }
        })
        
      })
    })
    return {
      target,
      isFixed,
      targetParent,
      portListData
    }
  }
  
  
}
</script>
<style lang="scss" scoped>
@import "@/assets/scss/_mixin.scss";
.project {
  position: relative;
  padding-top:40vw;
  background: #fff;
  &__tit {
    position: absolute;
    top:50px;
    left:50%;
    transform: translateX(-50%);
    color:#fff;
     mix-blend-mode: difference; /* 텍스트와 배경의 색상을 반전시킴 */
     z-index: 10;
     &.fixed {
      position: fixed;
     }
  }
  &__item {
    width: 100%;
    height: 100vh;
    position: sticky;
    top:0;
    left:0;
  }
  &__link {
    display: block;
    width:100%;
    height: 100%;
    padding: 14px 14px;
  }
  &__logo {
    margin-top: 14px;
  }
  &__num {
    position: absolute;
    top: 14px;
    left:14px;
    font-weight: 200;
  }
}
li {
  
}
</style>