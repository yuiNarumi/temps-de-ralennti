<template>
<div>
<Header />
  <full-page ref="fullpage" :options="options" id="fullpage">
    
      <!-- <p class="text">
        First section
      </p> -->
       <section id="top" class="section"></section>
    
    
      <section id="about" class="section about">
      <div class="about__container fadeContent">
        <div class="about__txtbox">
          <h2 class="about__ttl">About<br>Temps de ralenti</h2>
          <p class="about__txt">Temps de ralentiは<br>
                          デザインや快適さを通して、あなたの旅をより<br>
                          かけがえのない思い出にするデザインホテルです。</p>
        </div>
        <p class="about__pic"><img src="/aboutpic.jpg" alt="" class="about__img"></p>
          </div>
      </section>
    
    <!-- <div class="section">
      <p class="text">
        Third section
      </p>
    </div> -->

  <section id="stay" class="section stay">
                    

      <div class="stay__container fadeContent">

          <div id="b01" class="stay__wrapper">
          <div class="stay__box">
                            <p class="stay__pic"><img src="/room01.png" alt="room01" class="stay__img"></p>
                            <div class="stay__right">
                                <!-- <h2 class="stay__ttl">Stay</h2> -->
                                <p class="stay__sub">Room01</p>
                                <p class="stay__txt">Room01スタンダードルームはシンプルさの中にエレガントが光るデザインがあしらわれた空間。<br>全ての旅行者に快適さとリラクゼーションを捧げます。</p>
                                </div>
          </div>
          </div>
    
          <div id="b02" class="stay__wrapper">
                        <div class="stay__box">
                            <p class="stay__pic"><img src="/room02.jpg" alt="room02" class="stay__img"></p>
                            <div class="stay__right">
                                <!-- <h2 class="stay__ttl">Stay</h2> -->
                                <p class="stay__sub">Room02</p>
                                <p class="stay__txt">Room02で過ごす時間は、都会の喧騒を美しいパノラマへと変貌させます。<br>広く開放的な空間流れる穏やかなひとときをご堪能ください</p>
                                </div>
                        </div>
          </div>
    
          <div id="b03" class="stay__wrapper">
                        <div class="stay__box">
                            <p class="stay__pic"><img src="/room03.jpg" alt="room03" class="stay__img"></p>
                            <div class="stay__right">
                                <!-- <h2 class="stay__ttl">Stay</h2> -->
                                <p class="stay__sub">Room03</p>
                                <p class="stay__txt">あたたかな木の温もりがあなたを包み込みます。<br>異国のリゾートスパを感じるようなお部屋で、心ゆくまでゆったりとお過ごしください。</p>
                                </div>
                        </div>
          </div>

      </div>


  </section>

  <section id="rab" class="section rab">
                    <div class="fadeContent">
                    <h2 class="rab__ttl">Restaurant&Bar</h2>
                    <div class="rab__container">
                        <div class="rab__box">
                            <p class="rab__pic"><img src="/res.jpg" alt="restaurant" class="rab__img"></p>
                            <p class="rab__sub">Restaurant</p>
                            <p class="rab__more"><nuxt-link to="/restaurant" class="rab__link">Read more</nuxt-link></p>
                        </div>

                        <div class="rab__box">
                            <p class="rab__pic"><img src="/bar.jpg" alt="restaurant" class="rab__img"></p>
                            <p class="rab__sub">Loby Bar</p>
                            <p class="rab__more"><nuxt-link to="/bar" class="rab__link">Read more</nuxt-link></p>
                        </div>
                        
                    </div>
                    </div>
                </section>

  <section id="around" class="section around">
                  <div class="fadeContent">
                    <h2 class="around__ttl">Around Temps de ralenti</h2>
                    <div class="around__bg"></div>
                    <p class="around__txt">観光スポット、アトラクション、ショッピングモール、高級ナイトライフ、そして近所が提供する文化的および娯楽活動を発見してください。</p>

                  </div>
                </section>

  <section id="reserve" class="section section6">
    <div class="section6__container fadeContent">
                    <h2 class="section6__ttl">時の流れがゆったりと減速していくこの空間で<br>忘れられない一時を貴方に</h2>
                    <div class="section6__bg">
                        <ul class="section6__list">
                            <li class="section6__more"><nuxt-link to="/reservePage" class="section6__link">今すぐ予約する</nuxt-link></li>
                            <!-- <li class="section6__more"><a href="" class="section6__link">Googleマップでアクセスを確認</a></li> -->
                        </ul>
                    </div>
    </div>
                </section>

  </full-page>
</div>
</template>

<script>
import Header from '@/components/header.vue';
export default {
  name: 'IndexPage',
  cpmponents: {
    Header
  },
  data() {
                return {
                    current: 1
                }
            },
            mounted() {
                this.init();
                this.doObserve('.stay__wrapper');
                Typekit.load({async: true})
                const hash = this.$route.hash
                if (hash && hash.match(/^#.+$/)) {
                  this.$scrollTo(hash)
                }
            },
            methods: {
                init()  {
                    const targets = document.querySelectorAll('.stay__wrapper');
                    Array.from(targets).forEach((target,index) => {
                        if (index[0]) {
                            target.style.left = 0;
                        } else {
                            target.style.left = (index * 100) + '%';
                        }
                    });
                },
                doObserve(element) {
                    const targets = document.querySelectorAll(element);
                    const options = {
                        root: this.$refs.stay,
                        rootMargin: '0px',
                        threshold: 0.25
                    };
                    const observer = new IntersectionObserver((items) => {
                        items.forEach((item) => {
                            if (item.isIntersecting) {
                                item.target.classList.add('observed');
                                if(item.target.id === 'b01') {
                                    this.current = 1;
                                } else if(item.target.id === 'b02') {
                                    this.current = 2;
                                } else if(item.target.id === 'b03') {
                                    this.current = 3;
                                
                                }
                            } else {
                                item.target.classList.remove('observed');
                            }
                        });
                    }, options);
                    Array.from(targets).forEach((target) => {
                        observer.observe(target);
                    });
                },

            }
}
</script>

<style lang="scss">

$font-sub: noto-sans, sans-serif;

$font-ttl:monotype-modern-display, sans-serif;

$font-jp: a-otf-ryumin-pr6n, serif;


img {
    width: 100%;
    height: 100%;
}

@mixin ttlStyle {
    font-size: 96px;
      font-family: $font-ttl;
            font-weight: 400;
            font-style: normal;
            margin-bottom: 130px;
            color: #4c2f21;
}

@mixin txtStyle {
        font-family: $font-jp;
        font-weight: 300;
        font-size: 20px;
          letter-spacing: 0.2rem;
          line-height: 1.3;
}

section {
  position: relative;
  background: rgb(248, 234, 222);
  
  &:nth-child(1) {
  /* background-color: lightblue; */
  background: url(/mv-2.jpg)center center / cover;
  }

}

.about {
  
  &__container {
    width: 1440px;
    display: flex;
    justify-content: space-between;
    margin: 0 auto;
  }

  &__ttl {
      @include ttlStyle;
    }

     &__txt {
        @include txtStyle;
    }

  &__pic {
      width: 700px;
      height: 500px;
      background: #ddd;
    }
}

.stay {

    height: 100vh;
    overflow:hidden;
    position: relative;
    padding-top: 50px;

    &:after {
        content:"Stay";
        display: inline-block;
        position: absolute;
        top: 23%;
        right: 70px;
        z-index:0;
        @include ttlStyle;
    }
     

      &__container {
          position: relative;
        width: 100%;
        height: 100vh;
        scroll-snap-type: x mandatory;
        overflow-y:hidden;
        overflow-x:auto;
        scroll-behavior: smooth;
        position: relative;

        
    }
    
    &__wrapper {
          width: 100%;
          height: 100vh;
          position: absolute;
         top: 0;
         left: 0;
          display: flex;
          justify-content: space-between;
          align-items: center;
          scroll-snap-align:start;
          
      }

      &__box {
          width: 100%;
          height: 650px;
          display: flex;
          justify-content: space-between;
          align-items: center;
          padding: 0 70px;
      }

      &__pic {
          width: 1150px;
          height: 650px;
          border:1px solid #000;
      }

      &__right {
        width: 550px;
        height: 415px;
          display: flex;
          flex-direction: column;
          /* justify-content: space-between; */
          align-items: center;
          justify-content: center;
        align-self: flex-end;
        background: rgb(226, 213, 207);
      }


    //   &__ttl {
    //       position: absolute;
    //       top: 0;
    //       right: 0;
    //       z-index:5;
    //     @include ttlStyle;
    //   }
      

    //   &__roombox {
    //     // width: 550px;
    //     height: 415px;
        
    //     display: flex;
    //     flex-direction: column;
    //     // justify-content: center;
    //     // align-items: center;
    //     // background: rgb(226, 213, 207);
    //   }

      &__sub {
          font-family: $font-ttl;
          font-size: 80px;
          text-align: center;
          color: #4c2f21;
          margin-bottom: 0px;
      }

      &__txt {
          width: 350px;
          @include txtStyle;
      }
  }

  .rab {
        padding: 0 70px;
        /* padding-top: calc(90px + 30px); */

      &__ttl {
          align-self: flex-start;
          @include ttlStyle;
      }

      &__container {
          width: 100%;
          display: flex;
          justify-content: space-between;
          align-items: center;
          margin: 0 auto;
      }

      &__box {
          display: flex;
          flex-direction: column;
      }

      &__pic {
          width: 760px;
          height: 430px;
          background: #aaa;
          margin-bottom: 30px;
      }

      &__sub {
          font-family: $font-ttl;
          font-size: 48px;
          margin-bottom: 30px;
          color: #4c2f21;
      }

      &__more {
          align-self: flex-end;
      }

      &__link {
          font-family: $font-sub;
          font-weight: 300;
          font-size: 16px;
          text-decoration: none;
      }
  }

.around {
    /* padding-top: calc(90px + 30px); */
      &__ttl {
          text-align: right;
          padding-right: 240px;
          @include ttlStyle;
      }

      &__bg {
          width: 1680px;
          height: 520px;
          background: url(/aroundbg.jpg)center center / cover;
          align-self: flex-start;
          margin-bottom: 60px;
      }

      &__txt {
        align-self: flex-start;
        font-family: $font-jp;
        font-weight: 300;
        padding-left: 240px;
      }
  }

  .section6 {
    

    &__container {
      width: 100%;
      display: flex;
    }
    &__ttl {
        position: absolute;
        top: 50%;
        left: 70px;
        transform:translateY(-50%);
        font-size: 64px;
        line-height: 1.3;
        z-index:2;
        /* @include ttlStyle; */
        font-family: $font-jp;
        font-weight: 300;
        color: #4c2f21;
    }
    &__bg {
        width: 1680px;
          height: 520px;
        background: url(/sec6bg.jpg)center center / cover;
          position: absolute;
          right: 0;
          top: 50%;
          transform:translateY(-50%);
          margin-bottom: 60px;
    }

    &__list {
        position: absolute;
        top: 80%;
        list-style-type: none;
        display: flex;
        font-size: 20px;
        gap: 80px;
        font-family: $font-jp;
        font-weight: 300;
    }

    &__link {
      text-decoration: none;
      color: #4c2f21;
    }
    
  }
/* .text {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  opacity: 0;
  font-size: 240px;
} */

.fadeContent {
   opacity: 0;
}

@keyframes fadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

.active .fadeContent {
  animation-name: fadeIn;
  animation-duration: 0.5s;
  animation-delay: 0.75s;
  animation-fill-mode: forwards;
}
</style>