<template>
  <section ref="introBox" class="intro section-unit">
     <!--글자가 좌우로 사라지고 , 뒤에 배경이 나온다. 그리고 그걸 덮으면서 콘텐츠가 올라오기.-->
      <div class="intro__inner">
        <p ref="intro1" class="intro__txt it-1">Welcome</p>
        <p ref="intro2" class="intro__txt it-2">My Portfolio</p>
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
   const introBox = ref(null)
   const intro1 = ref(null)
   const intro2 = ref(null)
    onMounted(()=>{
      nextTick(()=>{
        const main = document.querySelector('main')
        const contact = document.querySelector('.contact')
        const introTimeline = gsap.timeline({
        scrollTrigger: {
          trigger: introBox.value,
          start: "top top",
          end: "+=300",
          scrub: 0.8,
          pin:true,
          // markers:true
        }
      });
      introTimeline.to(intro1.value,{
        xPercent:-100,
        duration:1
      })
      introTimeline.to(intro2.value,{
        xPercent:100,
        duration:1
      },0)
      introTimeline.to(introBox.value,{
        // yPercent:-100,
        background:"#fff",
        duration:1,
      },1)
      console.log(introTimeline)
        gsap.utils.toArray(".intro__txt").forEach((item, i) => {
        gsap.fromTo(item, {
          clipPath: "inset(0% 0% 100% 0%)",
          y: 25,
          letterSpacing:"-50px"
        }, {
          duration: .8,
          clipPath: "inset(0% 0% 0% 0%)",
          y: 0,
          letterSpacing:"0",
          delay: (i * 0.4)
          });
        });
      })
    })
    return {
      introBox,
      intro1,
      intro2
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
  height: 100vh;
  background: #000;
  overflow-x: hidden;
  &__inner {
    width: 100%;
    text-align: center;
  }
  &__txt {
    font-weight: 200;
    font-size:80px;
    text-transform: uppercase;
    color: #fff;
    transform-origin: left center;
  }
 }
</style>