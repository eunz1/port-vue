<script setup>
import IntroPart from '@/components/IntroPart.vue'
import MacUiPart from '@/components/MacUiPart.vue'
import SubTitlePart from '@/components/SubTitlePart.vue'
import ContactPart from '@/components/ContactPart.vue'
import ProfilePart from '@/components/ProfilePart.vue'
import ProjectPart from '@/components/ProjectPart.vue'
import ProjectTablePart from '@/components/ProjectTablePart.vue'
import Skip from '@/components/SkipPart.vue'
import Header from '@/components/HeaderPart.vue'
import Footer from '@/components/FooterPart.vue'
import { onMounted, nextTick } from 'vue';
import Lenis from "@studio-freight/lenis";

const scrollAnimation = () => {
  nextTick(() => {
    const wrapper = document.querySelector('html');
    console.log(wrapper)
    if (wrapper) {
      const lenis = new Lenis({
        wrapper:wrapper,
        duration: 1,
        easing: (t) => Math.min(1, 1.001 - Math.pow(2, -10 * t)),
        direction: "vertical",
        gestureDirection: "vertical",
        smooth: true,
      });

      function raf(time) {
        lenis.raf(time);
        requestAnimationFrame(raf);
      }

      requestAnimationFrame(raf);

      lenis.on("scroll", (e) => {
      });
    } else {
      console.error('Element not found');
    }

    //mouse effect
    const handleMouse = (e) =>{
      const cursor =document.querySelector('#mouse-cursor');
      const hover = document.querySelectorAll('.cursor-hover')
      const { clientX: posX, clientY: posY } = e;
       window.requestAnimationFrame(() => {
         cursor.style.left = `${posX - 20}px`,
        cursor.style.top = `${posY - 20}px`  
       })
      // console.log(posX, posY,e.pageX, e.pageY)
    }
    const handleHover = (e)=>{
      const cursor =document.querySelector('#mouse-cursor');
      document.querySelectorAll('a').forEach(link=>{
        link.addEventListener('mouseover',()=>{
          cursor.classList.add('hover-type')
        })
        link.addEventListener('mouseout',()=>{
          cursor.classList.remove('hover-type')
        })
      })
    }
    document.addEventListener('mousemove', handleMouse);
    handleHover();
  });
};

onMounted(() => {
  scrollAnimation();
  
});
</script>

<template>
<div class="wrap">
  <!-- <MacUiPart/> -->
  <SubTitlePart/>
  <main>
    <IntroPart/>
    <ProfilePart/>
    <ProjectPart/>
    <ProjectTablePart/>
    <ContactPart/>
    <!-- <Footer/> -->
  </main>
  <div id="mouse-cursor">
    <span class="cursor-txt">
      Click!
    </span>
  </div>
</div>
  
</template>
<style lang="scss" scoped>
.wrap {
  font-family: 'Pretendard';
  // overflow-x: hidden;

}
#mouse-cursor {
  position: fixed;
  width: 20px;
  height: 20px;
  background: #ce666b;
  border-radius: 999px;
  mix-blend-mode: difference;
  pointer-events: none;
  z-index: 999;
  transition: top 0.025s ease, left 0.025s ease, transform 0.25s ease, width 0.35s ease, height 0.35s ease;
  text-align: center;
  .cursor-txt {
    opacity: 0;
    transition: opacity 0.025s ease;
  }
  &.hover-type {
    width:50px;
    height: 50px;
    background: #ff7f84;
    .cursor-txt {
      opacity: 1;
      
      font-size: 10px;;
    }
  }
}



</style>
