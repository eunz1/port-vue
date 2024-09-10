<template>
  <div class="sub-title lobster" ref="subTitle">
    Intro
  </div>
</template>
<script>
import { ref, onMounted, nextTick } from 'vue';
import { gsap } from 'gsap';
import ScrollTrigger from 'gsap/ScrollTrigger';
gsap.registerPlugin(ScrollTrigger);
export default {
  setup() {
    const subTitle= ref(null)
    onMounted(()=>{
      const sections = gsap.utils.toArray('.section-unit');
      const titles = ['Intro','Profile','Project','Summary','Contact'];
      sections.forEach((section, i)=>{
        ScrollTrigger.create({
          trigger:section,
          start:'top top',
          end: i===0?'+=250':'bottom 50%',
          scrub: true,
          
          onEnter: () => {
            console.log(i)
            const index = sections.indexOf(section);
            subTitle.value.textContent = titles[index];
          },
          onEnterBack: () => {
            const index = sections.indexOf(section);
            subTitle.value.textContent = titles[index];
          }
        })
      })
    })
    return {
      subTitle
    }
  }
}
</script>
<style lang="scss" scoped>
  .sub-title {
    position: fixed;
    left: 50%;
    transform: translate(-50%);
    top: 60px;
    font-size: 30px;
    z-index: 10;
    color:#fff;
    mix-blend-mode: difference;
  }
</style>