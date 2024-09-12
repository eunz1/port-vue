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
        // requestAnimationFrame(raf);
      }

      // requestAnimationFrame(raf);

      lenis.on("scroll", (e) => {
      });
    } else {
      console.error('Element not found');
    }
  });
};

onMounted(() => {
  // scrollAnimation();
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
</div>
  
</template>
<style lang="scss" scoped>
.wrap {
  font-family: 'Pretendard';
  // overflow-x: hidden;

}
main {

}



</style>
