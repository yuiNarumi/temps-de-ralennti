<template>
<div>
    <SubHeader />
    <div class="bar">
        <div class="bar__bg">
        <h2 class="bar__ttl">Bar</h2>
        </div>
    </div>

    <div class="explanation">
            <p class="explanation__read">11 Mirrors Rooftop Restaurantのパノラマダイニングでは、ウクライナの最高の料理人がシームレスに織り交ぜた数多くのトレードマークの料理を提供し、繊細な汎アジアのフュージョンのタッチで現代的なヨーロッパ料理とウクライナ料理の両方を提供しています。ボルシチやチキンキエフなどの文化的な古典に加えて、メニューには、旅行者や地元の人々の間でその正当な位置を獲得しているさまざまな世界的なヒットが含まれています。</p>
            <p class="explanation__barpic"><img src="/barpic.jpg" alt="" class="explanation__barimg"></p>
    </div>

    <div class="barTime">
            <h2 class="barTime__ttl">営業時間</h2>
            <div class="barTime__txtBox">
                 <ul class="barTime__list">
                <li>日曜日-木曜日<span>17:00 — 00:00 (L.O. 11:30)</span></li>
                <li>金曜日-土曜日<span>17:11 — 02:00 (L.O. 01:30)</span></li>
            </ul>
            </div>
        </div>

        <p class="barMore"><nuxt-link to="/restaurant" class="barLink">レストランのページはこちらから</nuxt-link></p>
</div>
</template>

<script>
import SubHeader from'@/components/subheader.vue';
export default {
    components: {
        SubHeader
    },
    mounted() {
        Typekit.load({async: true})
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

.bar {
    
    &__bg {
        width: 100%;
        height: 100vh;
        background: url(/bar.jpg)center center / cover;
        position: relative;
        margin-bottom: 300px;
    }

    &__ttl {
        @include ttlStyle;
        color: #fff;
        position: absolute;
        bottom: -10%;
        right: 10%;
        z-index:2;
    }
}
 .explanation {
        width: 1500px;
        display: flex;
        justify-content: space-between;
        margin: 0 auto 300px;

    &__barpic {
        width: 800px;
        height: 400px;
        background: #ddd;
        
    }

    &__barimg {
        object-fit:cover;
    }

    &__read {
        @include txtStyle;
        width: 400px;
        line-height: 1.8;
    }

    }

    .barTime {
        width: 1500px;
        height: 500px;
        background: linear-gradient(261deg, rgba(51,32,22,1) 0%, rgba(24,57,95,0.5144651610644257) 100%);
        box-shadow:0px 0px 20px #fff inset;
        display: flex;
        flex-direction:row-reverse;
        flex-wrap:wrap;
        justify-content: space-between;
        margin-bottom: 150px;
        padding: 0 70px;

        &__ttl {
            @include ttlStyle;
            font-family: $font-jp;
            color: #fff;
            text-align: right;
            margin: 70px 0 0 0;
        }

        &__txtBox {
            align-self: flex-end;
            margin-bottom: 70px;
        }

        &__list {
            /* display: flex; */
            font-size: 20px;
            font-family: $font-jp;
            list-style:none;
           color: #fff;

            span {
                 font-size: 16px;
                margin-left: 30px; 
            }

            li {
                @include txtStyle;
                font-size: 20px;
                 padding-bottom: 20px;

                 &:last-of-type {
                     padding-bottom: 0;
                 }
            }
        }
    }

    .barMore {
        text-align: center;
        margin-bottom: 150px;
    }
    .barLink {
        font-size: 48px;
        font-family: $font-jp;
        color: #4c2f21;
        text-decoration: none;
    }
</style>