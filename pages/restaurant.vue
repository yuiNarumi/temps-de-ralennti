<template>
<div>
    <SubHeader />
    <div class="restaurant">
        <div class="restaurant__bg">
        <h2 class="restaurant__ttl">Restaurant</h2>
        </div>
    </div>
        <div class="explanation">
            <p class="explanation__read">11 Mirrors Rooftop Restaurantのパノラマダイニングでは、ウクライナの最高の料理人がシームレスに織り交ぜた数多くのトレードマークの料理を提供し、繊細な汎アジアのフュージョンのタッチで現代的なヨーロッパ料理とウクライナ料理の両方を提供しています。ボルシチやチキンキエフなどの文化的な古典に加えて、メニューには、旅行者や地元の人々の間でその正当な位置を獲得しているさまざまな世界的なヒットが含まれています。</p>
            <p class="explanation__respic"><img src="/respic.jpg" alt="" class="explanation__resimg"></p>
        </div>

        <div class="time">
            <h2 class="time__ttl">営業時間</h2>
            <div class="time__txtBox">
           
           
            <ul class="time__list">
                <li>朝食<br><span>6:30～10:00</span></li>
                <li>ランチ<br><span>11:30～14:00(L.O.)</span></li>
                <li>アフターランチ<br><span>14:00～17:00(L.O.)</span></li>
                <li>ディナー<br><span>17:00～22:00(L.O.)</span></li>
            </ul>
            
            <p class="time__txt">清掃と消毒のため休業<br><span>月曜日から金曜日:10:15 - 11:15</span></p>
            </div>
        </div>

        <p class="resMore"><nuxt-link to="/bar" class="resLink">バーのページはこちらから</nuxt-link></p>
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

.restaurant {
    &__bg {
        width: 100%;
        height: 100vh;
        background: url(/res.jpg)center center / cover;
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

    &__respic {
        width: 800px;
        height: 400px;
        background: #ddd;
        
    }

    &__read {
        @include txtStyle;
        width: 400px;
        line-height: 1.8;
    }

    }

    .time {
        width: 1500px;
        height: 500px;
        background: linear-gradient(261deg, rgba(210,112,44,1) 0%, rgba(226,167,162,0.5144651610644257) 100%);
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
            display: flex;
            gap: 40px;
            color: #4c2f21;
            margin-bottom: 70px;
        }

        &__list {
            font-size: 20px;
            font-family: $font-jp;
            list-style:none;
           

            span {
                 font-size: 16px;
                margin-left: 60px; 
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

        &__txt {
            @include txtStyle;
            font-size: 20px;
            align-self: flex-end;
            margin-bottom: 20px;

            span {
                font-size: 16px;
            }
        }
    }

    .resMore {
        text-align: center;
        margin-bottom: 150px;
    }

     .resLink {
        font-size: 48px;
        font-family: $font-jp;
        color: #4c2f21;
        text-decoration: none;
        
    }

</style>