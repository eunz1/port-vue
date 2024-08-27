<template>
  <section class="contact section-unit">
      <div class="contact__img">
        <img src="" alt="">
      </div>
      <div class="contact__txt">
       저에게 궁금한 점이 있으시거나, <br> 함께 일하고 싶으시다면 <br>
       아래 링크를 통해 메일을 보내주세요! 🥳
       <div class="contact__mail">
          <a href="mailto:songisjivv@gmail.com" class="lobster">CONTACT ME</a>
       </div>
      </div>
  </section>
</template>
<style lang="scss" scoped>
@import "@/assets/scss/_mixin.scss";
.contact {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 90vh;
  margin-top: 100px;
  text-align: center;
  &__txt {
    font-size: 2vw;
    @include mobile {
      font-size: 4vw;
    }
  }
  &__mail {
    position: relative;
    margin-top: 20px;
    font-size: 5vw;
    a {
      position: relative;
      &:after {
        position: absolute;
        bottom:0;
        left:0;
        width: 0;
        height: 2px;
        background: #000;;
        transition: 0.3s ease all;
        content: '';
      }
      &:hover {
        &:after {
          width: 100%;
        }
      }
    }
  }
}
</style>
