<template>
  <section class="contact section-unit">
      <div class="contact__img">
        <img src="" alt="">
      </div>
      <div class="contact__txt">
       <div class="contact__mail">
          <a href="mailto:songisjivv@gmail.com" class="lobster">CONTACT ME</a>
       </div>
      </div>
  </section>
</template>
<style lang="scss" scoped>
@import "@/assets/scss/_mixin.scss";
.contact {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  text-align: center;
  background: #000;;
  // background-image:url('../assets/Images/bg_contact.gif');
  // background-repeat: no-repeat;
  // background-attachment: fixed;
  // background-position: center;
  // background-size: cover;
  &:before {
    position: absolute;
    top:50%;
    left:50%;
    transform: translate(-50%,-50%);
    width:300px;
    height:450px;
    background-image:url('../assets/Images/bg_contact.gif');
    background-repeat: no-repeat;
    // background-attachment: fixed;
    background-position: center;
    background-size: cover;
    
    content:''
  }
  &:after {
    position: absolute;
    top:0;
    left:0;
    width:100%;
    height: 100%;
    background: rgba(0,0,0,0.5);
    pointer-events: none;;
    content:'';
  }
  &__txt {
    font-size: 2vw;
    mix-blend-mode: difference;
    color: #fff;;
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
        background: #fff;;
        mix-blend-mode: difference;
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
