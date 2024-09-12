<template>
  <div class="marquee-wrapper" ref="wrapper">
    <div class="marquee" ref="marquee">
      <div class="marquee-content" ref="marqueeText">
        <slot></slot>
      </div>
    </div>
  </div>
</template>
<script>
import { ref, onMounted, onBeforeUnmount, nextTick } from 'vue';
import { gsap } from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';
gsap.registerPlugin(ScrollTrigger);
export default {
  setup(){
    const wrapper = ref(null);
    const marquee = ref(null);
    const marqueeText = ref(null);
    const marqueeCount = 2;
    let marqueeWidth = 0;
    let tl = null;

    const createMarqueeAnimation =() => {
      if (!marquee.value || !wrapper.value) return;
      const target = marqueeText.value.children[0];
      marqueeWidth = target.offsetWidth;
      marqueeText.value.style.setProperty('--marquee-distance', `-${marqueeWidth}px`);
      for( let i = 0; marqueeCount > i ; i++ ){
        let copyItem = target.cloneNode(true);
        target.after(copyItem)
      }
    }
    const handleResize = () => {
      const target = marqueeText.value.children[0];
       marqueeWidth = target.offsetWidth;
       marqueeText.value.style.setProperty('--marquee-distance', `-${marqueeWidth}px`);
    };
    onMounted(() => {
      createMarqueeAnimation();
      window.addEventListener('resize', handleResize);
    });

    onBeforeUnmount(() => {
      // window.removeEventListener('resize', handleResize);
    });
    return {
      wrapper,
      marquee,
      marqueeText,
      marqueeCount,
      marqueeWidth
    } ;
  }
  
}
</script>
<style lang="scss">

.marquee {
  // position: fixed;
  top:50%;
  display: flex;
  align-items: center;
  width: 100%;
  &-wrapper {
    overflow: hidden;
    white-space: nowrap;
    position:sticky;
    top: 50%;
    z-index: 0;
    opacity: 0.3;
    margin-top: 50vh;
  }
  &-content {
    display: flex;
    white-space: nowrap;
    animation-name: marquees-1;
    animation-iteration-count: infinite;
    animation-timing-function: linear;
    transition-property: opacity;
    transition-timing-function: cubic-bezier(.4,0,.2,1);
    animation-duration: 40s;
    font-size: 5vw;
    -webkit-text-stroke: 1px;
    -webkit-text-stroke-color: #000;
    color: #fff;
    & >* {
      padding: 0 10px;
    }
  }
  @keyframes marquees-1 {
  0% { transform: translate3d(0, 0, 0) }
    100% { transform: translate3d(var(--marquee-distance), 0, 0) }
  }
}

</style>
