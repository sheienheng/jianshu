<template>
    <div>
        <my-header :headcount="headCount"></my-header>
        <div class="index my-container">
            <div class="row">
                <div class="col-8 main">
                    <!--轮播图-->
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
                    <!--推荐专题-->
                    <div class="recommend-collection">
                        <nuxt-link to="/collection/123">
                            <img src="/img/collection1.png" alt="">
                            <span>旅行.在路上</span>
                        </nuxt-link>
                        <nuxt-link to="/collection/123">
                            <img src="/img/collection2.jpg" alt="">
                            <span>故事</span>
                        </nuxt-link>
                        <nuxt-link to="/collection/123">
                            <img src="/img/collection3.jpg" alt="">
                            <span>人文社科</span>
                        </nuxt-link>
                        <nuxt-link to="/collection/123">
                            <img src="/img/collection1.png" alt="">
                            <span>读书</span>
                        </nuxt-link>
                        <nuxt-link to="/collection/123">
                            <img src="/img/collection2.jpg" alt="">
                            <span>社会热点</span>
                        </nuxt-link>
                        <nuxt-link to="/collection/123">
                            <img src="/img/collection3.jpg" alt="">
                            <span>手绘</span>
                        </nuxt-link>
                        <nuxt-link to="/collection/123">
                            <img src="/img/collection2.jpg" alt="">
                            <span>社会热点</span>
                        </nuxt-link>
                        <nuxt-link to="/collection/123">
                            <img src="/img/collection3.jpg" alt="">
                            <span>@IT互联网</span>
                        </nuxt-link>
                        <nuxt-link to="/collection/123" class="more-hot-collection">
                            更多热门专题
                            <i class="fa fa-angle-right"></i>
                        </nuxt-link>
                    </div>
                    <div class="split-line"></div>
                    <!--文章列表-->
                    <div id="list-container">
                        <ul class="note-list">
                            <li class="have-img">
                                <nuxt-link class="warp-img" to="/p/_id">
                                    <img src="../assets/img/note1.jpg" alt="">
                                </nuxt-link>
                                <div class="content">
                                    <div class="author">
                                        <nuxt-link to="/u/123" class="avatar">
                                            <img src="../assets/img/default-avatar.jpg" alt="">
                                        </nuxt-link>
                                        <div class="info">
                                            <nuxt-link to="/u/123" class="nickname">
                                                测试用户
                                            </nuxt-link>
                                            <span class="time">8小时前</span>
                                        </div>
                                    </div>
                                    <nuxt-link class="title" to="/p/123">
                                        如何把书中的只是转化为能力？这是我见过的做好的回答
                                    </nuxt-link>
                                    <p class="abstract">
                                        随着知识经济的兴起，读书的重要性得到了大家的普遍认同，
                                        于是市场上出现很多读书方法，比如速度、多读、慢读、列读……
                                        不管你采用哪一种读书方法，最终都要回归到“行动”二字上，正如陆...
                                    </p>
                                    <div class="meta">
                                        <nuxt-link to="/collection/123" class="collection-tag">
                                            短篇小说短篇小说短篇小说短篇小说短篇小说
                                        </nuxt-link>
                                        <nuxt-link to="/p/123" class="colorChange">
                                            <i class="fa fa-eye"></i>
                                            555
                                        </nuxt-link>
                                        <nuxt-link to="/p/123" class="colorChange">
                                            <i class="fa fa-comment"></i>
                                            200
                                        </nuxt-link>
                                        <span>
                                            <i class="fa fa-heart"></i>
                                            555
                                        </span>
                                    </div>
                                </div>
                            </li>
                            <li>
                                <div class="content">
                                    <div class="author">
                                        <nuxt-link to="/u/123" class="avatar">
                                            <img src="../assets/img/default-avatar.jpg" alt="">
                                        </nuxt-link>
                                        <div class="info">
                                            <nuxt-link to="/u/123" class="nickname">
                                                测试用户
                                            </nuxt-link>
                                            <span class="time">8小时前</span>
                                        </div>
                                    </div>
                                    <nuxt-link class="title" to="/p/123">
                                        如何把书中的只是转化为能力？这是我见过的做好的回答
                                    </nuxt-link>
                                    <p class="abstract">
                                        随着知识经济的兴起，读书的重要性得到了大家的普遍认同，
                                        于是市场上出现很多读书方法，比如速度、多读、慢读、列读……
                                        不管你采用哪一种读书方法，最终都要回归到“行动”二字上，正如陆...
                                    </p>
                                    <div class="meta">
                                        <nuxt-link to="/collection/123" class="collection-tag">
                                            短篇小说
                                        </nuxt-link>
                                        <nuxt-link to="/p/123" class="colorChange">
                                            <i class="fa fa-eye"></i>
                                            555
                                        </nuxt-link>
                                        <nuxt-link to="/p/123" class="colorChange">
                                            <i class="fa fa-comment"></i>
                                            200
                                        </nuxt-link>
                                        <span>
                                            <i class="fa fa-heart"></i>
                                            555
                                        </span>
                                    </div>
                                </div>
                            </li>
                            <li class="have-img">
                                <nuxt-link class="warp-img" to="/p/123">
                                    <img src="../assets/img/note1.jpg" alt="">
                                </nuxt-link>
                                <div class="content">
                                    <div class="author">
                                        <nuxt-link to="/u/123" class="avatar">
                                            <img src="../assets/img/default-avatar.jpg" alt="">
                                        </nuxt-link>
                                        <div class="info">
                                            <nuxt-link to="/u/123" class="nickname">
                                                测试用户
                                            </nuxt-link>
                                            <span class="time">8小时前</span>
                                        </div>
                                    </div>
                                    <nuxt-link class="title" to="/p/123">
                                        如何把书中的只是转化为能力？这是我见过的做好的回答
                                    </nuxt-link>
                                    <p class="abstract">
                                        随着知识经济的兴起，读书的重要性得到了大家的普遍认同，
                                        于是市场上出现很多读书方法，比如速度、多读、慢读、列读……
                                        不管你采用哪一种读书方法，最终都要回归到“行动”二字上，正如陆...
                                    </p>
                                    <div class="meta">
                                        <nuxt-link to="/collection/123" class="collection-tag">
                                            短篇小说短篇小说短篇小说短篇小说短篇小说
                                        </nuxt-link>
                                        <nuxt-link to="/p/123" class="colorChange">
                                            <i class="fa fa-eye"></i>
                                            555
                                        </nuxt-link>
                                        <nuxt-link to="/p/123" class="colorChange">
                                            <i class="fa fa-comment"></i>
                                            200
                                        </nuxt-link>
                                        <span>
                                            <i class="fa fa-heart"></i>
                                            555
                                        </span>
                                    </div>
                                </div>
                            </li>
                            <li>
                                <div class="content">
                                    <div class="author">
                                        <nuxt-link to="/u/123" class="avatar">
                                            <img src="../assets/img/default-avatar.jpg" alt="">
                                        </nuxt-link>
                                        <div class="info">
                                            <nuxt-link to="/u/123" class="nickname">
                                                测试用户
                                            </nuxt-link>
                                            <span class="time">8小时前</span>
                                        </div>
                                    </div>
                                    <nuxt-link class="title" to="/p/123">
                                        如何把书中的只是转化为能力？这是我见过的做好的回答
                                    </nuxt-link>
                                    <p class="abstract">
                                        随着知识经济的兴起，读书的重要性得到了大家的普遍认同，
                                        于是市场上出现很多读书方法，比如速度、多读、慢读、列读……
                                        不管你采用哪一种读书方法，最终都要回归到“行动”二字上，正如陆...
                                    </p>
                                    <div class="meta">
                                        <nuxt-link to="/collection/123" class="collection-tag">
                                            短篇小说
                                        </nuxt-link>
                                        <nuxt-link to="/p/123" class="colorChange">
                                            <i class="fa fa-eye"></i>
                                            555
                                        </nuxt-link>
                                        <nuxt-link to="/p/123" class="colorChange">
                                            <i class="fa fa-comment"></i>
                                            200
                                        </nuxt-link>
                                        <span>
                                            <i class="fa fa-heart"></i>
                                            555
                                        </span>
                                    </div>
                                </div>
                            </li>
                        </ul>
                    </div>
                    <!--阅读更多-->
                    <nuxt-link to="/" class="load-more">
                        阅读更多
                    </nuxt-link>
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
                    <div class="download">
                        <button type="button" class="btn btn-primary" title="Popover title"
                                data-container="body" data-toggle="popover" data-placement="top"
                                data-content="顶部的 Popover 中的一些内容">
                            顶部的 Popover
                        </button>
                    </div>
                    <!--推荐作者-->
                    <div class="recommend-author">
                        <div class="title">
                            <span>推荐作者</span>
                            <a href="javascript:void(0)" class="page-change" @click="rotate()">
                                <i class="fa fa-refresh" ref="refresh"></i>
                                换一批
                            </a>
                        </div>
                        <ul class="list">
                            <li>
                                <nuxt-link to="/u/123" class="avatar">
                                    <img src="../assets/img/default-avatar.jpg" alt="">
                                </nuxt-link>
                                <nuxt-link class="follow" to="/u/123">
                                    <i class="fa fa-plus"></i>
                                    关注
                                </nuxt-link>
                                <nuxt-link class="name" to="/u/123">
                                    战小狼
                                </nuxt-link>
                                <p>
                                    写了111.8K字 7K喜欢
                                </p>
                            </li>
                            <li>
                                <nuxt-link to="/u/123" class="avatar">
                                    <img src="../assets/img/default-avatar.jpg" alt="">
                                </nuxt-link>
                                <nuxt-link class="follow" to="/u/123">
                                    <i class="fa fa-plus"></i>
                                    关注
                                </nuxt-link>
                                <nuxt-link class="name" to="/u/123">
                                    战小狼
                                </nuxt-link>
                                <p>
                                    写了111.8K字 7K喜欢
                                </p>
                            </li>
                            <li>
                                <nuxt-link to="/u/123" class="avatar">
                                    <img src="../assets/img/default-avatar.jpg" alt="">
                                </nuxt-link>
                                <nuxt-link class="follow" to="/u/123">
                                    <i class="fa fa-plus"></i>
                                    关注
                                </nuxt-link>
                                <nuxt-link class="name" to="/u/123">
                                    战小狼
                                </nuxt-link>
                                <p>
                                    写了111.8K字 7K喜欢
                                </p>
                            </li>
                            <li>
                                <nuxt-link to="/u/123" class="avatar">
                                    <img src="../assets/img/default-avatar.jpg" alt="">
                                </nuxt-link>
                                <nuxt-link class="follow" to="/u/123">
                                    <i class="fa fa-plus"></i>
                                    关注
                                </nuxt-link>
                                <nuxt-link class="name" to="/u/123">
                                    战小狼
                                </nuxt-link>
                                <p>
                                    写了111.8K字 7K喜欢
                                </p>
                            </li>
                            <li>
                                <nuxt-link to="/u/123" class="avatar">
                                    <img src="../assets/img/default-avatar.jpg" alt="">
                                </nuxt-link>
                                <nuxt-link class="follow" to="/u/123">
                                    <i class="fa fa-plus"></i>
                                    关注
                                </nuxt-link>
                                <nuxt-link class="name" to="/u/123">
                                    战小狼
                                </nuxt-link>
                                <p>
                                    写了111.8K字 7K喜欢
                                </p>
                            </li>
                        </ul>
                        <nuxt-link to="/" class="find-more">
                            查看更多
                            <i class="fa fa-angle-right"></i>
                        </nuxt-link>
                    </div>
                </div>
            </div>
        </div>
        <footer class="my-container">
            <div class="row">
                <div class="col-8 foot">
                    <nuxt-link to="/">
                        关于简书
                    </nuxt-link>
                    <span>·</span>
                    <nuxt-link to="/">
                        联系我们
                    </nuxt-link>
                    <span>·</span>
                    <nuxt-link to="/">
                        加入我们
                    </nuxt-link>
                    <span>·</span>
                    <nuxt-link to="/">
                        简书出版
                    </nuxt-link>
                    <span>·</span>
                    <nuxt-link to="/">
                        品牌与徽标
                    </nuxt-link>
                    <span>·</span>
                    <nuxt-link to="/">
                        帮助中心
                    </nuxt-link>
                    <span>·</span>
                    <nuxt-link to="/">
                        合作伙伴
                    </nuxt-link>
                    <div>
                        我很强
                    </div>

                </div>
                <div class="col-4">

                </div>
            </div>
        </footer>
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
          },
          deg:360,
          headCount:0,
        }
      },
      mounted() {
      },
      methods:{
        rotate:function(){
          this.deg = this.deg + 360;
          this.$refs.refresh.style.transform = `rotate(${this.deg}deg)`;
        },

      }

    }
</script>
<style>

</style>