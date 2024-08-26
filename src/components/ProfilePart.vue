<template>
  <section class="profile" ref="profileBox">
      <div class="profile__tit lobster" ref="profileTit">Profile</div>
      <div class="profile__inner" ref="profilePhoto">
        <div class="profile__photo">
          <figure>
            <div class="photo-box">
              <img src="@/assets/images/my_pic.png" alt="프로필 사진">
            </div>
            <figcaption>
              <p class="profile__balloon">"기획과 개발 사이를 튼튼하게 이어주는 꼼꼼한 퍼블리싱을 하는 퍼블리셔 입니다"<span class="triangle"></span></p>
              <span class="tag-tit lobster">Skills</span>
              <ul>
                <li>
                   <span class="tag">HTML5</span>
                </li>
                <li>
                   <span class="tag">CSS</span>
                </li>
                <li>
                   <span class="tag">Javascript/Jquery</span>
                </li>
                <li>
                   <span class="tag">Vue.js</span>
                </li>
                <li>
                </li>
                <li>
                   <span class="tag-tit lobster">Tools</span>
                   <span class="tag">Git</span>
                   <span class="tag">Photoshop</span>
                   <span class="tag">Figma</span>
                   <span class="tag">Zeplin</span>
                </li>
              </ul>
            </figcaption>
          </figure>
        </div>
        <ul class="profile__cont" ref="profileCont">
          <li><span class="num">2016.2</span> 수원대학교 사학과 졸업</li>
          <li><span class="num">2016.2 </span>컴퓨터활용능력 2급 취득</li>
          <li><span class="num">2017.1 ~ 2017.5  </span>봄아카데미: 웹퍼블리셔 양성과정 수료 </li>
          <li><span class="num">2017.12 ~ 2021.12  </span>웹에이전시: 디파이(DFY) <br> 4년 0개월 근무</li>
          <li><span class="num">2019.11 </span>정보처리기사 취득</li>
          <li><span class="num">2022.01 ~ 2024.04 </span>   명품판매 이커머스: 오케이몰(OKmall)<br>2년 4개월 근무</li>
        </ul>
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
    const profileBox = ref(null)
    const profileTit = ref(null)
    const profilePhoto = ref(null)
    const profileCont = ref(null)
    onMounted(()=>{
      nextTick(()=>{
        const main = document.querySelector('main')
        const project = document.querySelector('.project')
        const listItems = profileCont.value.querySelectorAll('li');


        gsap.to(profileTit,{

        })
        //이력 등장 
        listItems.forEach((item, index) => {
          gsap.to(item, {
            opacity: 1,
            y: 0,
            duration: 0.3,
            scrollTrigger: {
              scroller:main,
              trigger: item,
              start: 'top 80%', 
            },
          });
        });  
        //   gsap.fromTo(main,{
        //   backgroundColor:"rgb(0,0,0)",
        //   scrollTrigger: {
        //    trigger: profileBox.value,
        //     scroller:main,
        //     scrub:1,
        //     start:"bottom 50%",
        //     end:"bottom 20%",
        //     markers:true
        //   },
        //     onUpdate:()=>{console.log('??')}
        // })
        //  gsap.to(profileBox.value,{
        //   scrollTrigger: {
        //     trigger:profileBox.value,
        //     scroller:main,
        //     scrub:true,
        //     pin:true,
        //     start:"top center",
        //     end:`+=${profileBox.value.clientHeight}`,
        //     markers:true
        //   },
        // })
       
        
      })
    })
    return {
      profileBox,
      profileTit,
      profilePhoto,
      profileCont
    }
  }
  
  
}
</script>
<style lang="scss" scoped>
@import "@/assets/scss/_mixin.scss";
 .profile{
   padding:50px 0;
  &__tit{
    position: sticky;
    top: 0;
    font-size: 30px;
    text-align: right;
    transform: translateY(0%);
    z-index: 1;
  }
  &__inner {
    &:after {
    clear: both;
    content: '';
   }
  } 
  &__photo {
    position: sticky;
    top:15px;
    width: 25%;
    height:calc(91vh - 30px);
    padding: 15px;
    border-radius: 4px;
    float: left;
    font-size: clamp(14px, 1.5vw, 18px);
    @include mobile {
      position: static;
      width: 100%;
      height: auto;
      float:none;
      font-size: clamp(16px, 7vw, 25px);
    }
    figure {
      padding: 0 10px;
      figcaption { 
        padding-top: 20px;
        text-align: center;
        word-break: keep-all;
        border-radius: 0;
        span{
          display: block;
          margin-bottom: 10px;
          text-align: center;
        }
      }
    }
    .photo-box {
      position: relative;
      border-radius: 50%;
      overflow: hidden;
      background: #bec6bb;;
      max-width: 300px;
      max-height: 300px;
      @include mobile {
        width: 200px;
        height: 200px;
        margin: 0 auto;
        padding-top: 0;
      }
      img {
        width:100%;
      }
    }
     .tag {
        font-size: 14px;
        &-tit {
          position: relative;
          display: inline-block;
          font-size: 20px;
         
          &::after {
            position: absolute;
            left:0;
            bottom:0;
            width: 100%;
            height: 1px;
            background: #000;;
            content:'';
          }
        }
      }
  }
  &__balloon {
    position: relative;
    top:-36px;
    left:50%;
    transform: translateX(-50%);
    max-width: 255px;
    padding: 4px;
    background: #fff;;
    font-size: 13px;
    border-radius: 5px;;
    .triangle {
      position: absolute;
      top: 0;
      left:50%;
      transform: translate(-50%,-100%);
      width: 10px;
      height: 10px;
      background-color: transparent;
      &:after {
        content: '';
        position: absolute;
        top: 0;
        left: 0;
        width: 0;
        height: 0;
        border-left: 5px solid transparent;
        border-right: 5px solid transparent;
        border-bottom: 10px solid #fff;
      }
    }
  }

  &__cont {
    width: 75%;
    margin-left:auto;
    text-align: center;
    @include mobile {
      width: 100%;
    }
    li {
      position: relative;
      display: flex;
      flex-direction: column;
      justify-content: center;
      height: 15vh;
      margin-bottom: 100px;
      opacity: 0;
      &:last-child {
        margin-bottom: 0;;
      }
      @include mobile {
        height: auto;
      }
      &::after {
        position: absolute;
        top:100%;
        left:50%;
        width: 1px;
        height: 80px;
        background: #585858;
        content: '';
      }
      &:last-child {
        &:after {
          display: none
        };
      }
      .num {
        display: block;
        font-family:  var(--mainNum-font);;
      }
     
    }
  }
 }
</style>