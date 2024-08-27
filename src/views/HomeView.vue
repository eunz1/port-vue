<script setup>
import IntroPart from '@/components/IntroPart.vue'
import MacUiPart from '@/components/MacUiPart.vue'
import SubTitlePart from '@/components/SubTitlePart.vue'
import ContactPart from '@/components/ContactPart.vue'
import ProfilePart from '@/components/ProfilePart.vue'
import ProjectPart from '@/components/ProjectPart.vue'
import Skip from '@/components/SkipPart.vue'
import Header from '@/components/HeaderPart.vue'
import Footer from '@/components/FooterPart.vue'
import { onMounted, nextTick } from 'vue';
import Lenis from "@studio-freight/lenis";

const scrollAnimation = () => {
  nextTick(() => {
    const wrapper = document.querySelector('main');
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
  });
};

onMounted(() => {
  scrollAnimation();
});
</script>

<template>
<div class="wrap">
  <MacUiPart/>
  <SubTitlePart/>
  <main>
    <IntroPart/>
    <ProfilePart/>
    <ProjectPart/>
    <ContactPart/>
    <Footer/>
  </main>
</div>
  
</template>
<style lang="scss" scoped>
.wrap {
  display: flex;
  justify-content: center;
  // align-items: center;
  box-sizing: border-box;
  // background: #000;
  height: 100vh;
}
main {
  width: calc(100% - 30px);
  height: calc(100% - 68px);
  margin-top: 53px;
  padding: 0 15px;
  overflow-x: hidden;
  overflow-y: scroll;
  border-radius: 0 0 10px 10px;
  box-shadow: 6px -8px 20px 20px rgba(0, 0, 0, 0.35);
  // background: #c4bfb9;
  background: #d8cbc5;
  scrollbar-width: none; /* Firefox */
  -ms-overflow-style: none; /* IE and Edge */
  &::-webkit-scrollbar {
    display: none; /* Chrome, Safari, Opera */
  }
}



</style>
