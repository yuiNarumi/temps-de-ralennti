<template>
<div class="header">

    <div class="toggle" @click="isActive01=!isActive01">
        <span class="toggle__top" :class="{topRotate:isActive01}"></span>
        <span class="toggle__bottom" :class="{bottomRotate:isActive01}"></span>
    </div>

    <h1 class="header__ttl">Temps de ralenti<br><span>Design Hotel</span></h1>

    <p class="header__reserve"><nuxt-link to="/reservePage" class="header__link">Reserve</nuxt-link></p>

    <nav class="gnav" :class="{navOpacity:isActive01}">
                <ul class="gnav__list">
                    <li><nuxt-link to="/" @click="isActive01=!isActive01">About</nuxt-link></li>
                    <li><nuxt-link to="/" @click="isActive01=!isActive01">Stay</nuxt-link></li>
                    <li><nuxt-link to="/" @click="isActive01=!isActive01">Restaurant & Bar</nuxt-link></li>
                    <li><nuxt-link to="/" @click="isActive01=!isActive01">Around</nuxt-link></li>
                    <li><nuxt-link to="/" @click="isActive01=!isActive01">Reserve</nuxt-link></li>
                    <li><nuxt-link to="/reservePage" @click="isActive01=!isActive01">ご予約する</nuxt-link></li>
                </ul>
    </nav>
</div>
</template>

<script>
export default {
   
    data () {
    return {
        name: "",
        isActive01: false
        }
    }

}
</script>

<style lang="scss">

$font-sub: noto-sans, sans-serif;

$font-ttl:monotype-modern-display, sans-serif;

$font-jp: a-otf-ryumin-pr6n, serif;

.header {
    width: 100%;
    position: fixed;
    top: 0;
    left: 0;
    z-index:10;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: rgba(170, 170, 170,.6);
    padding: 20px 70px;

    &__ttl {
        font-size: 25px;
            letter-spacing: 0.05em;
            line-height: 1;
            font-family: $font-ttl;
            font-weight: 400;
            font-style: normal;
            text-align: center;

            span {
                 font-size: 20px;
            }
    }


    &__link {
        text-decoration: none;
        font-family: $font-jp;
        font-size: 20px;
        color: #000;
    }
}

.toggle {
    width: 35px;
    height: 35px;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    z-index:12;

    &__top,
    &__bottom {
        display: inline-block;
        width: 35px;
        height: 2px;
        background: #000;
        transition:.4s;
    }

    &__top {
        transform:translateY(-5px);
    }

    &__bottom {
        transform:translateY(5px);
    }
}
.gnav {
    width: 100%;
    height: 100vh;
    position: absolute;
    top: 0;
    left: 0;
    z-index:11;
    display: flex;
    justify-content: center;
    align-items: center;
    background: rgba(204, 204, 204, 0.85);
    opacity: 0;
    transition:.4s;
    pointer-events:none;

    &:after {
        content:"Temps de ralenti";
        font-size: 102px;
        font-family: $font-ttl;
        letter-spacing: 0.2rem;
        position: absolute;
        bottom: 60px;
        right: 60px;
        color: #4c2f21;
    }

    &__list {
        display: flex;
        list-style: none;
        gap: 30px;
        font-family: $font-jp;
        font-size: 28px;
        
        a {
            text-decoration: none;
            color: #4c2f21;
        }
    }
    
}

.topRotate{
    transform:rotate(45deg);
}
.bottomRotate {
    transform:rotate(-45deg);
}

.navOpacity {
    opacity: 1;
    pointer-events: visible;
}
</style>