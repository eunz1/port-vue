<template>
  <section ref="introBox" class="intro section-unit">
      <div class="intro__inner">
        <div class="mac-box">
          <!-- <div class="mac-box__toolbar">
            <span class="circle"></span>
            <span class="circle"></span>
            <span class="circle"></span>
          </div> -->
          <h1>
            <p ref="introText1" class="lobster">EUNJI' s PortFolio</p>
            <p ref="introText2" class="lobster">
              <span class="mont">안녕하세요, 제 포트폴리오를 방문해주셔 감사합니다.</span><br>
              Explore My Publishing Journey!
            </p>
          </h1>
        </div>
      </div>
  </section>
</template>
<script>
import { ref, onMounted, nextTick } from 'vue';
import { gsap } from 'gsap';
import ScrollTrigger from 'gsap/ScrollTrigger';
gsap.registerPlugin(ScrollTrigger);
export default {
  setup() {
   const introText1 = ref(null)
   const introText2 = ref(null)
   const introBox = ref(null)
    onMounted(()=>{
      nextTick(()=>{
        const main = document.querySelector('main')
        const contact = document.querySelector('.contact')
        console.log(contact)
        gsap.to(introText1.value,{
          opacity:1,
          translateY:0,
          duration:0.5,
          ease: "power1.inOut",
        })
        gsap.to(introText2.value,{
          opacity:1,
          translateY:0,
          duration:0.5,
          delay:0.5,
          ease: "power1.inOut",
        })
        gsap.to(main,{
          scrollTrigger: {
            trigger:introBox.value,
            scroller:main,
            scrub:true,
            start:"top top",
            end:`+=${introBox.value.clientHeight}`,
          },
            backgroundColor:"#f3ede8",
        })
      })
    })
    return {
      introText1,
      introText2,
      introBox
    }
  }
  
  
}
</script>
<style lang="scss" scoped>
 .intro {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
  h1 {
    // color:#fff;
    text-align: center;
    p {
      transform: translateY(30px);
      opacity: 0;
      font-size: 3.5vw;
      color:#000;
      font-weight: bold;
      // text-transform: uppercase;
      will-change: transform;
      &:first-child {
        font-size: clamp(40px, 20vw, 120px);
        // font-family:  var(--mainNum-font);;
      }
    }

  }
 }
 
</style>