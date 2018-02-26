<template>
    <div>
        <my-header></my-header>
        <div class="my-container">
            <div class="row">
                <div class="main">
                    <div class="tag-banner">
                        <img src="../../assets/img/shoucang.png" alt="" style="width: 100%;margin-top: 20px;">
                    </div>
                    <!--收藏列表-->
                    <ul class="nost-list">
                        <li>
                            <div class="content">
                                <div class="author">
                                    <nuxt-link to="/u/123" class="avatar">
                                        <img src="../../assets/img/default-avatar.jpg" alt="">
                                    </nuxt-link>
                                    <div class="info">
                                        <nuxt-link to="/u/123" class="nickname">草根女王的简爱</nuxt-link>
                                        <span class="time">前天 15:31</span>
                                    </div>
                                </div>
                                <nuxt-link to="/p/123" class="title">
                                    《戏说网恋》
                                </nuxt-link>
                                <p class="abstract">
                                    打开视频两两望， 小心堕入千重浪。 烟花易冷江湖上， 人生大事需思量。 露水红颜祸水当， 风花雪月云烟往。 隐姓埋名尽伪装， 甜言蜜语耍计量。 情话连篇暖心房， 海誓山盟指月...
                                </p>
                                <div class="meta">
                                    <nuxt-link to="/p/123">
                                        <i class="fa fa-eye"></i> 84
                                    </nuxt-link>
                                    <nuxt-link to="/p/123">
                                        <i class="fa fa-comment"></i> 5
                                    </nuxt-link>
                                    <span>
                                  <i class="fa fa-heart"></i> 30
                              </span>
                                    <a href="javascript:void(0)" class="cancel">取消收藏</a>
                                </div>
                            </div>
                        </li>
                        <li class="have-img">
                            <div class="content">
                                <div class="author">
                                    <nuxt-link to="/u/123" class="avatar">
                                        <img src="../../assets/img/default-avatar.jpg" alt="">
                                    </nuxt-link>
                                    <div class="info">
                                        <nuxt-link to="/u/123" class="nickname">关土</nuxt-link>
                                        <span class="time">02.07 03:00</span>
                                    </div>
                                </div>
                                <nuxt-link to="/p/123" class="title">
                                    此景只应天上有
                                </nuxt-link>
                                <p class="abstract">
                                    在岛上工作，每天上下班，坐车坐船至少要花去三个小时，好在“福利”好，每天路上总有惊喜。两周前的一天，我经历的一个惊喜，要是不分享一下，感觉就是犯罪。 那天清晨，坐渡轮上岛。 ...
                                </p>
                                <div class="meta">
                                    <nuxt-link to="/p/123">
                                        <i class="fa fa-eye"></i> 184
                                    </nuxt-link>
                                    <nuxt-link to="/p/123">
                                        <i class="fa fa-comment"></i> 56
                                    </nuxt-link>
                                    <span>
                                  <i class="fa fa-heart"></i> 730
                              </span>
                                    <a href="javascript:void(0)" class="cancel">取消收藏</a>
                                </div>
                            </div>
                        </li>
                    </ul>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
  import myHeader from '../../components/myHeader'
  export default {
    name: 'myhomepage',
    components:{
      myHeader
    },
  }
</script>

<style scoped>
    .main{
        padding-top: 30px;
        margin-left: 12.5%;
        width: 75%;
    }
    .main .tag-banner{
        width: 100%;
        margin-bottom: 30px;
        min-height: 100px;
    }

    .main .nost-list li{
        position: relative;
        width: 100%;
        margin: 0 0 17px;
        padding: 0 2px 17px 0;
        border-bottom: 1px solid #f0f0f0;
        word-wrap: break-word;
    }
    .main .nost-list .author{
        margin-bottom: 7px;
        font-size: 13px;
    }
    .main .nost-list .author .avatar{
        display: inline-block;
        margin-right: 5px;
    }
    .main .nost-list .author .info{
        display: inline-block;
        vertical-align: middle;
    }
    .nost-list .author .info span{
        padding-left: 3px;
        color: #969696;
    }
    .nost-list .content .title{
        margin-bottom: 4px;
        font-size: 18px;
        font-weight: 700;
        display: inline-block;
    }
    .nost-list .abstract{
        margin-bottom: 8px;
        font-size: 13px;
        line-height: 24px;
    }
    .nost-list .meta{
        font-size: 12px;
        font-weight: 400;
        line-height: 20px;
        color: #b4b4b4;
    }
    .nost-list .meta a{
        margin-right: 10px;
    }
    .nost-list .meta span{
        margin-right: 10px;
    }
    .nost-list li.have-img{
        min-height: 140px;
    }
    .nost-list .have-img .wrap-img{
        position: absolute;
        right: 0;
        top:50%;
        margin-top: -68px;
        width: 150px;
        height: 120px;
    }
    .nost-list .have-img .wrap-img img{
        width: 100%;
        height: 100%;
        border-radius: 4px;
        border: 1px solid #f0f0f0;
    }
    .nost-list .have-img>div{
        padding-right: 160px;
    }


</style>