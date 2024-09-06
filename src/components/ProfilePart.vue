<template>
  <section class="profile section-unit" ref="profileBox">
      <!-- <div class="profile__tit lobster" ref="profileTit">Profile</div> -->
      <div class="profile__hello-wrap" ref="helloWrap">
        <div class="profile__hello" :class="{'blur':isEnter}" ref="helloMessage">
          <div class="hello-photo">
            <img :src="mypic" alt="아바타 사진">
          </div>
          <p >
            안녕하세요, 6년 4개월차 경력의 웹 퍼블리셔 송은지 입니다.
            기획과 디자인, 개발 사이를 잘 이어주는 꼼꼼한 UI/UX 구현을
            지향합니다. 
          </p>
        </div>
      </div>
      <ul ref="profileImg" class="profile__image">
        <li class="profile__image-item">
          <figure class="profile__image-img">
            <img :src="profileImg1" alt="프로필이미지1" ref="imgTarget">
          </figure>
          <figure class="profile__image-img">
            <img :src="profileImg2" alt="프로필이미지2" ref="imgTarget">
          </figure>
          <div class="profile__image-desc">
            <p>4년간의 웹에이전시, 2년 4개월의 중견기업 이커머스 운영 퍼블리셔로 근무했습니다 </p>
            <p>HTML, CSS3, SCSS, Jquery, JavaScript를 사용하며</p>
            <p>기획,디자인과는 Photoshop, Zeplin, Figma로 협업 했고 <br>팀 내에서는 Gitlab 사용하였습니다.</p>
          </div>
        </li>
        <li class="profile__image-item">
          <figure class="profile__image-img">
            <img :src="profileImg3" alt="프로필이미지3" ref="imgTarget">
          </figure>
          <figure class="profile__image-img">
            <img :src="profileImg4" alt="프로필이미지4" ref="imgTarget">
          </figure>
          <div class="profile__image-desc">
            <p>항상 밝은 모습으로 모든 사람들과 커뮤니케이션 하기를 즐기는 성격입니다.</p>
            <p>꼼꼼하고 </p>
            <p>생산성향상, 자기계발에 관심이 많으며 안주하지 않고 끊임없이 발전하는 모습 보여드리겠습니다.</p>
          </div>
        </li>
      </ul>
  </section>
</template>
<script>
import { ref, onMounted, nextTick } from 'vue';
import { gsap } from 'gsap';
import ScrollTrigger from 'gsap/ScrollTrigger';
gsap.registerPlugin(ScrollTrigger);
import mypic from "../assets/Images/my_pic.png"
import profileImg1 from "../assets/Images/profile_1.jpg"
import profileImg2 from "../assets/Images/profile_2.jpg"
import profileImg3 from "../assets/Images/profile_3.jpg"
import profileImg4 from "../assets/Images/profile_4.jpg"
export default {
  setup() {
    const profileBox = ref(null)
    const helloWrap = ref(null)
    const profileImg = ref(null)
    const helloMessage = ref(null)
    const imgTarget = ref([]);
    const isEnter = ref(false);
    onMounted(()=>{
      nextTick(()=>{
        const main = document.querySelector('main')
        const project = document.querySelector('.project')
        const imgArray = document.querySelectorAll('.profile__image-img')
        const HelloTL = gsap.timeline({
          // scrollTrigger: {
          //   trigger: helloWrap.value,
          //   start: "top 50%",
          //   // endTrigger: profileImg.value, // profileImg가 끝날 때 고정 해제
          //   end: "+=1000", // profileImg의 끝 지점에 고정 해제
          //   pin:true,
          //   scrub:0.5,
          //   markers:true,
          //   onEnter:()=>{
          //       // console.log('profile')
          //       setTimeout(()=>{
          //         isEnter.value = true
          //       },600)

          //   },
          //   onEnterBack:()=>{
          //     // console.log("ddd,")
          //     isEnter.value = true
          //   },
          //   onLeave:()=>{
          //     isEnter.value = false
          //     // console.log('end')
          //   },
          //   onLeaveBack:()=>{
          //     isEnter.value = false
          //   }
          // }
        })
        gsap.from(helloMessage.value,{
          yPercent:-50,
          opacity:0,
          duration:1,
          scrollTrigger: {
            trigger:helloMessage.value,
            start: "top 70%",
            end:"bottom 65%",
            // markers:true,
            scrub:1
          }
        })
        imgArray.forEach((item, index) => {
          gsap.to(item.querySelector('img'), {
            yPercent: 10,
            delay: (index * 0.4),
            scrollTrigger: {
              trigger: item,
              start: "top 80%",
              end: "bottom top",
              scrub: true,
              // markers: true
            }
          });
        });
        // HelloTL.to(profileImg.value,{
        //   yPercent:-100,
        //   ease:"none",
        //   duration:1
        // })
      })
    })
    return {
      isEnter,
      profileBox,
      profileImg,
      helloWrap,
      helloMessage,
      mypic,
      profileImg1,
      profileImg2,
      profileImg3,
      profileImg4,
      imgTarget
    }
  }
  
  
}
</script>
<style lang="scss" scoped>
@import "@/assets/scss/_mixin.scss";
 .profile{
  background: #fff;
   padding:50px 0;
  //  background: lime;
   &__hello {
      display: grid;
      grid-template-columns: repeat(12, 1fr);
      font-size: 2rem;
      font-weight: 200;
      &.blur {
        opacity: 0.5!important;
      }
      &-wrap {
        // height: 100vh;
      }
      & > p {
         grid-column: span 6;
      }
      .hello-photo {
        grid-column: 2/span 1;
        img {
          width: 100%;
        }
      }
   }
   &__image {
      padding: 0 14px;
      font-weight: 200;
      // background: #585858;
      img {transition: 0.3s ease all;}
      &-item {
        display: grid;
        grid-template-columns: repeat(12,1fr);
        padding-top: 20vw;
        &:first-child {
          .profile__image-img {
            &:nth-child(2) {
              margin-top: 10vw;
              grid-column: 6/span 3;
            }
          }
        }
        &:nth-child(2) {
          margin-top: 20vw;
          .profile__image-img {
            &:nth-child(2) {
              margin-top: 25vw;
              grid-column: 7/span 3;
            }
          }
        }
      }
      
      &-img {
        grid-column: 2/span 3;
      }
      &-desc {
        grid-column: 10/span 3;
        word-break: keep-all;
      }
   }
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
      max-width: 300px;
      max-height: 300px;
      margin:0 auto;
      background: #bec6bb;;
      border-radius: 50%;
      overflow: hidden;
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
    padding: 14px;
    background: #fff;;
    font-size: 13px;
    border-radius: 5px;;
    @include mobile {
      padding: 8px;
    }
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
      margin-top: 50px;
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
        margin-bottom: 5px;
        font-size: 14px;
        color:#585858;
        font-family:  var(--mainNum-font);;
      }
     
    }
  }
 }
</style>