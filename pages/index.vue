<template>
    <div>
        <my-header></my-header>
        <div class="index my-container">
            <div class="row">
                <div class="col-8 main">
                    <!--轮播图-->
                    <div v-swiper:mySwiper="swiperOption">
                        <div class="swiper-wrapper banner">
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
                            <img src="../assets/img/right-1.png" alt="">
                        </nuxt-link>
                        <nuxt-link to="/">
                            <img src="../assets/img/right-2.png" alt="">
                        </nuxt-link>
                        <nuxt-link to="/">
                            <img src="../assets/img/right-3.png" alt="">
                        </nuxt-link>
                        <nuxt-link to="/">
                            <img src="../assets/img/right-4.png" alt="">
                        </nuxt-link>
                        <nuxt-link to="/">
                            <img src="../assets/img/right-5.png" alt="">
                        </nuxt-link>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
    import myHeader from '../components/myHeader'
    export default{
      components:{
        myHeader
      },
      data(){
        return{
          banners:[
            "/img/lunbo1.jpg",
            "/img/lunbo2.jpg",
            "/img/lunbo3.jpg",
            "/img/lunbo4.jpg",
            "/img/lunbo5.jpg",
          ],

          swiperOption: {
            loop: true,
            slidesPerView: 'auto',
            centeredSlides: true,
            spaceBetween: 30,
            autoplay: {
              delay:3000,
              stopOnLastSlide:false,//是否停止在做后一张
              disableOnInteraction:false//触碰后自动切换也不会停止
            },
            pagination: {
              el: '.swiper-pagination'
            },
            navigation: {
              nextEl: '.swiper-button-next',
              prevEl: '.swiper-button-prev',
            },
          }
        }
      },
      mounted() {
      }

    }
</script>
<style>
    .swiper-button-next{
        background-color: rgba(0,0,0,.4);
    }
    .swiper-button-prev{
        background-color: rgba(0,0,0,.4);
    }
</style>