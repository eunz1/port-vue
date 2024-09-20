<template>
  <section ref="targetParent" class="project section-unit">
    <!-- <h2 class="project__tit" :class="{'fixed':isFixed}">Project</h2> -->
    <ul ref="target">
      <li  class="project__item" v-for="(item, index) in portListData" :key="index" :style="{backgroundColor: item.color}">
        <div class="project__item-dimd" ref="projectItem"></div>
        <strong class="project__num lobster" :style="{color:item.blackVersion ? '#000' : '#fff'}">( No.{{ index + 1 }} )</strong>
          <a :href="item.url" target="_blank" class="project__link">
            <div class="project__link-inner">
              <figure class="project__logo">
                <img :src="item.img" alt="">
              </figure>
              <div class="project__txt" :style="{color:item.blackVersion ? '#000' : '#fff'}" :class="item.blackVersion ? 'black-type' : ''">
                <dl>
                  <!-- <dt>프로젝트명</dt> -->
                  <dd>{{item.name}}</dd>
                </dl>
                <div class="project__txt-desc">
                  <p>
                    <span v-for="(desc, desc1) in item.desc" :key="desc1">
                      {{desc}}
                    </span>
                  </p>
                </div>
                <dl>
                  <dt>담당역할</dt>
                  <dd>{{item.role}}</dd>
                </dl>
                <dl>
                  <dt>업무기간</dt>
                  <dd>{{item.duration}}</dd>
                </dl>
                <dl>
                  <dt>사용스킬</dt>
                  <dd>{{item.stack}}</dd>
                </dl>
                <div class="project__go">
                    ( <span>View Detail </span>  )
                </div>
              </div>
              
            
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
    const projectItem = ref(null)
    const isFixed = ref(false)
    const portListData = ref([
      {
        name:'명품판매 이커머스 오케이몰 운영',
        role:'PL/PA',
        duration:'2022.01 ~ 2024.04 (2년 4개월)',
        desc:[
          '중견 이커머스 사이트 운영, 유지보수 퍼블리셔로',
          '고객단 사이트의 UI/UX 개선과 노후화된 페이지의 리뉴얼을 담당하였습니다'],
        stack:'HTML,CSS,JQUERY',
        img:logo1,
        url:'https://harmonious-fang-850.notion.site/4d816ff6bc46455a8fffcabacadb9465',
        text:'1',
        color:"#fff",
        blackVersion:true
      },
      { name:'MPX GALLERY 구축',
        role:'PA',
        desc:["MPX GALLERY의 art works들을 판매하는 페이지 구축 프로젝트입니다.","메인 페이지와 마이페이지 등을 맡아 작업하였습니다. "],
        duration:'2021.10 ~ 2021.12',
        stack:'HTML, SCSS ,JavaScript, gulp, tailwind',
        img:logo2,
        url:'https://harmonious-fang-850.notion.site/MPX-GALLERY-140fa891ed5d474e95893202abac2731',
        text:'2',
        color:"#0056A6",
        blackVersion:false
      },
      { name:'삼성 디지털프라자 프로젝트 구축',
        desc:['삼성 디지털프라자 관련 화면 구축 및 기존 판매사이트 유지보수 작업으로','키오스크 관리자 화면, 키오스크 고객단 화면, 카카오 웹 접속화면, 상담페이지 화면등을 작업 하였습니다.'],
        role:'PA',
        duration:'2021.8 ~ 2021.10',
        stack:'HTML, SCSS ,JavaScript, Gulp',
        img:logo3,
        url:'https://harmonious-fang-850.notion.site/09daae6abc8c4caea5bc721c03186071',
        text:'3',
        color:"#333",
        blackVersion:false
      },
      { name:'롯데 통합 e커머스 구축 및 운영',
        desc:['Vue2 환경에서 퍼블리싱 작업을 기반으로 한 프로젝트로, ','구축과 운영을 포함하여 18개월 동안 진행되었습니다.'],
        role:'PA',
        duration:'2019.07~ 2020.12 (1년 6개월)',
        stack:'Vue2, SCSS, JavaScript',
        img:logo4,
        url:'https://harmonious-fang-850.notion.site/LOTTE-ON-19e438e7fa574faabb9c918cc373bfa4',
        text:'4',
        color:"#C84D54",
        blackVersion:false
      }
      
    ])
    
    onMounted(()=>{
      nextTick(()=>{
        const main = document.querySelector('main')
        const targetChild = target.value;
        projectItem.value.forEach((item,i)=>{
          console.log(projectItem.value.length);
          gsap.to(item,{
            opacity: i===projectItem.value.length -1 ? 1 : 0.6,
            scrollTrigger:{
              trigger:item,
              start:"top top",
              end:"bottom top",
              scrub:true,
              // markers:true,

              onEnter:()=>{
              console.log(i + 'start')
              },
              onLeave:() =>{
              console.log(i)
              }
            }
            
          })
        })
        
      })
    })
    return {
      target,
      isFixed,
      targetParent,
      projectItem,
      portListData
    }
  }
  
  
}
</script>
<style lang="scss" scoped>
@import "@/assets/scss/_mixin.scss";
.project {
  position: relative;
  padding-top:0;
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
    position: sticky;
    top:0;
    left:0;
    height: 100vh;
    padding: 14px;
    &-dimd {
      width: 100%;
      height:100%;
      position: absolute;
      top:0;
      left:0;
      background: #000;
      opacity: 0;
      pointer-events: none;
    }

  }
  &__link {
    display: flex;
    align-items: center;
    justify-content: center;
    width:100%;
    height: 100%;
    &-inner {
      display: flex;
      flex-wrap: wrap;
      flex-direction: row;
      justify-content: center;
      width: 100%;
    }
  }
  &__logo {
    display: flex;
    align-items: center;
    justify-content: center;;
    width: 50%;
    margin: 14px auto 0;
    img {
      width: 80%;
    }
    @include mobile{
      width: 100%;
    }
  }
  &__num {
    position: relative;
    top: 46px;
    // left:14px;
    font-size: 20px;
    font-weight: 200;
    @include mobile{
      top: 58px;
      font-size: 15px;
    }
  }
  &__txt {
    display: flex;
    justify-content: center;
    flex-direction: column;
    width: 50%;
    font-weight: 200;
    @include mobile{
      width: 100%;
      margin-top:20px;
    }
    dl {
      margin-bottom:10px;
      text-align: center;
      dt {
        font-size: 12px;
        margin-bottom:5px;
      }
      &:first-child dd {
        font-size: 20px;
        font-weight: bold;
        @include mobile{
          font-size:15px;
        }
      }
    }
    &-desc {
      position: relative;
      padding-bottom: 50px;
      margin-top: 10px;
      text-align:center;
      span {
        display: block;
      }
      &:after {
        position: absolute;
        width: 1px;
        background: #fff;
        bottom: 10px;
        height: 35px;
        content:'';
        @at-root .black-type & {
          background: #000;
        }
      }
    }
  }
  &__go {
    display: flex;
    justify-content: center;
    margin-top:14px;
    font-weight: 200;
    font-size: 20px;
  }
}
li {
  
}
</style>