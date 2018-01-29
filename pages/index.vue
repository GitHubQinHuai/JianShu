<template xmlns:v-swiper="http://www.w3.org/1999/xhtml">
    <div>
        <my-header></my-header>
        <div class="index my-container">
            <div class="row">
                <div class="col-8 main">
                    <!--banner-->
                    <div v-swiper:mySwiper="swiperOption" class="banner">
                        <div class="swiper-wrapper">
                            <div class="swiper-slide" v-for="banner in banners">
                                <img :src="banner">
                            </div>
                        </div>
                        <div class="swiper-pagination swiper-pagination-white"></div>
                        <div class="swiper-button-prev swiper-button-white"></div>
                        <div class="swiper-button-next swiper-button-white"></div>
                    </div>
                </div>
                <div class="col-4 aside">
                    <div class="board">
                        <nuxt-link to="/">
                            <img src="../assets/img/aside/aside001.png"">
                        </nuxt-link>
                        <nuxt-link to="/">
                            <img src="../assets/img/aside/aside002.png"">
                        </nuxt-link>
                        <nuxt-link to="/">
                            <img src="../assets/img/aside/aside003.png"">
                        </nuxt-link>
                        <nuxt-link to="/">
                            <img src="../assets/img/aside/aside004.png"">
                        </nuxt-link>
                        <nuxt-link to="/">
                            <img src="../assets/img/aside/aside005.png"">
                        </nuxt-link>

                    </div>
                </div>
            </div>
        </div>
    </div>                
</template>

<script>
    import myHeader from '../components/myHeader'
    export default {
        name: "index",
        components:{
            myHeader
        },
        data(){
            return{
                banners:[
                    '/banner001.jpg',
                    '/banner002.jpg',
                    '/banner003.jpg',
                    '/banner004.jpg'
                ],
                swiperOption: {
                    autoplay:{
                        delay:3000,
                        stopOnLastSlide:false,//是否停止在最后一张
                        disableOnInteraction:false,//禁止轮播
                    },
                    pagination: {
                        el: '.swiper-pagination',
                        dynamicBullets: true
                    },
                    navigation: {
                        nextEl: '.swiper-button-next',
                        prevEl: '.swiper-button-prev'
                    },
                    on: {
                        slideChange() {
                            console.log('onSlideChangeEnd', this);
                        },
                        tap() {
                            console.log('onTap', this);
                        }
                    }
                }
            }
        },
    }
</script>
<style>

</style>