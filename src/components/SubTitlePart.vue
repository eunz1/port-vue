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
      const main = document.querySelector('main')
      const sections = gsap.utils.toArray('.section-unit');
      const titles = ['Intro','Profile','Project','contact'];
      sections.forEach((section, i)=>{
        ScrollTrigger.create({
          scroller:main,
          trigger: section,
          start: i === 2 ? "top 25%" : i ===3 ?"bottom 50% ":'top top',
           end: i === 3 ? 'right right' : 'bottom top',
          scrub: true,
          onEnter: () => {
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
    right: 25px;
    top: 60px;
    font-size: 30px;
    z-index: 10;
  }
</style>