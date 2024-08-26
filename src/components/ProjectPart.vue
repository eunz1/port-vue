<template>
  <section ref="targetParent" class="project">
    <ul ref="target">
      <li v-for="(item, index) in portListData" :key="index">
        <strong class="project__num lobster">{{ index + 1 }}</strong>
          <a :href="item.url" target="_blank">
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
    const portListData = ref([
      {
        name:'명품판매 이커머스 오케이몰 운영',
        role:'PL/PA',
        duration:'2022.01 ~ 2024.04 (2년 4개월)',
        stack:'HTML,CSS,JQUERY',
        img:logo1,
        url:'https://harmonious-fang-850.notion.site/4d816ff6bc46455a8fffcabacadb9465',
        text:'1',
      },
      { name:'MPX GALLERY 구축',
        role:'PA',
        duration:'2021.10 ~ 2021.12',
        stack:'HTML, SCSS ,JavaScript, gulp, tailwind',
        img:logo2,
        url:'https://harmonious-fang-850.notion.site/MPX-GALLERY-140fa891ed5d474e95893202abac2731',
        text:'2'
      },
      { name:'삼성 디지털프라자 프로젝트 구축',
        role:'PA',
        duration:'2021.8 ~ 2021.10',
        stack:'HTML, SCSS ,JavaScript, Gulp',
        img:logo3,
        url:'https://harmonious-fang-850.notion.site/09daae6abc8c4caea5bc721c03186071',
        text:'3'
      },
      { name:' 롯데 통합 e커머스 구축 및 운영',
        role:'PA',
        duration:'2019.07~ 2020.12 (1년 6개월)',
        stack:'Vue2, SCSS, JavaScript',
        img:logo4,
        url:'https://harmonious-fang-850.notion.site/LOTTE-ON-19e438e7fa574faabb9c918cc373bfa4',
        text:'4'
      }
      
    ])
    
    onMounted(()=>{
      nextTick(()=>{
        const main = document.querySelector('main')
        const targetChild = target.value;
        let targetWidth =  targetChild.offsetWidth;
        console.log(targetChild.offsetWidth, main.offsetWidth)
        let amountScroll =  targetWidth - main.offsetWidth

         gsap.to(target.value, {
          x: -amountScroll,
          scrollTrigger: {
            trigger: targetParent.value,
            scroller:main,
            start: "top 25%",
            end: "+="+amountScroll,
            scrub: true, 
            pin:true,
            
          },
          duration: 2
        });
        //   gsap.to(main,{
        //   scrollTrigger: {
        //    trigger: targetParent.value,
        //     scroller:main,
        //     scrub:true,
        //     start:"top bottom",
        //     end:"bottom"+"+="+amountScroll,
           
        //     markers:true
        //   },
        //     onUpdate:()=>{console.log('??')}
        // })
        
       
      })
    })
    return {
      target,
      targetParent,
      portListData
    }
  }
  
  
}
</script>
<style lang="scss" scoped>

 section {
  margin-top: 100px;
 }
  ul {
    display: flex;
    width:fit-content;
    height: 50vh;
    // overflow: hidden;
    will-change: transform;
    li {
      position: relative;
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      width: 60vw;
      flex-shrink: 0;
      padding: 0 20px;
      margin: 0 20px;
      background: #a6a998;
      border-radius: 10px;
      box-shadow: 0px 16px 20px 4px rgba(0, 0, 0, 0.3);
      &:nth-child(2) {
      }
      &:nth-child(3) {
      }
      &:nth-child(2) {
      }
      // margin-right:1vw;
    }
  }
  .project {
    &__num {
      display: block;
      font-size: 6vh;
      position: absolute;
      top:0;
      left:30px;
      transform: translateY(-50%);
    }
    &__logo {
      position: relative;
      padding-top: 50%;
      img {
        position: absolute;
        top:0;
      }
    }
    &__txt {
      dl {
        display: flex;
        margin-top:10px;
        dt {
          width: 30%;
        }
      }
    }
  }
</style>