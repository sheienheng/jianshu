<template>
    <div>
        <my-header></my-header>
        <div class="note">
            <!--文章区域-->
            <div class="post">
                <!--正文-->
                <div class="article">
                    <h1 class="title">
                        雪中的聆听
                    </h1>
                    <div class="author">
                        <nuxt-link to="/u/123" class="avatar">
                            <img src="../../assets/img/default-avatar.jpg" alt="">
                        </nuxt-link>
                        <div class="info">
                            <span class="name">测试用户</span>
                            <!--<a href="#" class="btn-sm follow" v-if="followShow" @click="followShow=!followShow">-->
                                <!--<i class="fa fa-plus"></i>-->
                                <!--关注-->
                            <!--</a>-->
                            <!--<a href="#" class="btn-sm follow checkchange" v-if="!followShow" @click="followShow=!followShow"-->
                            <!--@mouseenter="followMes=false" @mouseleave="followMes=true">-->
                                <!--<span v-show="followMes">-->
                                    <!--<i class="fa fa-check"></i>-->
                                    <!--已关注-->
                                <!--</span>-->
                                <!--<span v-show="!followMes" >-->
                                    <!--<i class="fa fa-close"></i>-->
                                    <!--取消关注-->
                                <!--</span>-->
                            <!--</a>-->
                            <a class="btn-sm" href="javascript:void(0)" :class="followObj" @click="isFollow" @mouseover="noFollow" @mouseleave="beFollow">
                                <i class="fa" :class="iconObj" ref="icon"></i>
                                <span ref="followWord">关注</span>
                            </a>
                            <div class="meta">
                                <span>2018.01.23 16:09</span>
                                <span>字数 2273</span>
                                <span>阅读 882</span>
                                <span>评论 7</span>
                                <span>喜欢 9</span>
                            </div>
                        </div>
                    </div>
                    <div data-note-content="" class="show-content">
                        <div style="width: 100%;margin-bottom: 20px;">
                            <img src="../../assets/img/xue.jpg" alt="" style="width: 100%;">
                        </div>
                        <p>迷乱的风雪</p>
                        <p>模糊了天与地</p>
                        <p>嶙峋的枝头</p>
                        <p>排着一行麻雀</p>
                        <p>仿佛入定</p>
                        <p>这一刻的世界</p>
                        <p>万籁俱静</p>
                        <p>静静地</p>
                        <p>我在聆听</p>
                        <p>听到了</p>
                        <p>静静的你</p>
                        <p>壁炉中绽放的火星</p>
                        <p>是轻轻地叮咛</p>
                        <p>好像有沙沙声</p>
                        <p>那是你手中的书卷在唱歌</p>
                        <p>静静地</p>
                        <p>我听到了你心头飘过的诗行</p>
                        <p>我听到你笑了</p>
                        <p>笑得那么宁静</p>
                        <p>不要打扰你</p>
                        <p>是我静静地决定</p>
                        <hr>
                    </div>
                    <div class="show-foot">
                        <nuxt-link to="/nb/123" class="notebook">
                            <i class="fa fa-book"></i>
                            我的文集
                        </nuxt-link>
                        <div class="copyright">
                            ©著作权归作者所有
                        </div>
                    </div>
                    <div class="follow-detail">
                        <div class="info">
                            <nuxt-link class="avatar" to="/u/123">
                                <img src="../../assets/img/default-avatar.jpg" alt="">
                            </nuxt-link>
                            <a class="btn" href="javascript:void(0)" :class="followObj" @click="isFollow" @mouseover="noFollow" @mouseleave="beFollow">
                                <i class="fa" :class="iconObj" ref="icon2"></i>
                                <span ref="followWord2">关注</span>
                            </a>
                            <nuxt-link to="/u/123" class="title">
                                测试用户
                            </nuxt-link>
                            <i class="fa fa-mars"></i>
                            <div class="meta">
                                <span>2018.01.23 16:09</span>
                                <span>字数 2273</span>
                                <span>阅读 882</span>
                                <span>评论 7</span>
                                <span>喜欢 9</span>
                            </div>
                        </div>
                        <div class="signature">
                            俯首拜阳明，仰止惟佛陀。
                        </div>


                    </div>
                    <div class="meta-bottom">
                        <div class="like">
                            <div class="btn like-group" ref="islikeshow">
                                <div class="btn-like" @click="islike">
                                    <a href="javascript:void(0)">
                                        <i class="fa fa-heart"></i>
                                        <span>喜欢</span>
                                    </a>
                                </div>
                                <div class="modal-wrap">
                                    <a href="javascript:void(0)">{{islikeCount}}</a>
                                </div>
                            </div>

                        </div>
                        <div class="share-group">
                            <a href="#" v-b-tooltip.hover  title ="分享到微博">
                                <i class="fa fa-weibo weibo"></i>
                            </a>
                            <a href="#" v-b-tooltip.hover  title ="分享到微信">
                                <i class="fa fa-weixin weixin"></i>
                            </a>
                            <a href="#" v-b-tooltip.hover  title ="下载长微博图片">
                                <i class="fa fa-picture-o pic"></i>
                            </a>
                            <!--<a href="javascipt:void(0)" class="more-share" v-b-tooltip.click  title ="下载长微博图片">-->
                                <!--更多分享-->
                            <!--</a>-->
                            <!--<a href="javascipt:void(0)" class="more-share" @click.stop="moreShow">-->
                                <!--更多分享-->
                                <!--<span class="more-share-show" ref="moreMsg">-->
                                    <!--<p>分享的QQ空间</p>-->
                                    <!--<p>分享的QQ空间</p>-->
                                    <!--<p>分享的QQ空间</p>-->
                                    <!--<p>分享的QQ空间</p>-->
                                    <!--<div class="sanjiao"></div>-->
                                <!--</span>-->

                            <!--</a>-->
                            <a class="more-share" href="javascript:void(0)" id="popoverButton-sync" variant="primary">
                                更多分享
                            </a>
                            <b-popover :show.sync="showPop" target="popoverButton-sync" placement="top" triggers="focus">
                                <ul class="share-list">
                                    <li>
                                        <a href="javascript:void(0)">
                                            <i class="fa fa-twitter twitter"></i>
                                            <span>分享到Twitter</span>
                                        </a>
                                    </li>
                                    <li>
                                        <a href="javascript:void(0)">
                                            <i class="fa  fa-facebook-square facebook"></i>
                                            <span>分享到Facebook</span>
                                        </a>
                                    </li>
                                    <li>
                                        <a href="javascript:void(0)">
                                            <i class="fa fa-google-plus google"></i>
                                            <span>分享到Google</span>
                                        </a>
                                    </li>
                                </ul>
                            </b-popover>

                        </div>
                    </div>
                </div>
                <!--回复组件-->
                <my-comment></my-comment>
            </div>
            <!--悬浮的操作框-->
            <div class="side-bar">
                222222222222
            </div>
            <!--对应的推荐阅读-->
            <div class="note-bottom">
                33333333
            </div>
        </div>

    </div>

</template>

<script>
  import myHeader from '../../components/myHeader'
  import myComment from '../../components/myComment'
  export default {
    name: 'Id',
    data(){
      return{
        followObj:{
          'follow':true,
          'following':false
        },
        iconObj:{
          'fa-plus':true,
          'fa-check':false
        },
        islikeCount:35,
        msg:'fdfsdfc',
        isshareShow:true,
        showPop:false
      }
    },
    components:{
      myHeader,
      myComment
    },
    methods:{
      // moreShow:function(event){
      //   // event.stopPropagation();
      //   this.isshareShow = false;
      //   this.$refs.moreMsg.style.cssText="visibility: visible";
      // },
      // moreShow2:function(){
      //   this.isshareShow = true;
      //   this.$refs.moreMsg.style.cssText="visibility: hidden";
      // },
      isFollow:function(){
        this.followObj.follow = !this.followObj.follow;
        this.followObj.following = !this.followObj.following;
        this.iconObj['fa-plus'] = !this.iconObj['fa-plus'];
        this.iconObj['fa-check'] = !this.iconObj['fa-check'];
        let word = this.$refs.followWord.innerHTML;
        this.$refs.followWord.innerHTML = word == '关注' ? '已关注' : '关注';
        this.$refs.followWord2.innerHTML = word == '关注' ? '已关注' : '关注';
      },
      noFollow:function(){
        let word = this.$refs.followWord.innerHTML;
        if(word == '已关注'){
          this.$refs.followWord.innerHTML = '取消关注';
          this.$refs.icon.className = 'fa fa-close';
          this.$refs.followWord2.innerHTML = '取消关注';
          this.$refs.icon2.className = 'fa fa-close';
        }
      },
      beFollow:function(){
        let word = this.$refs.followWord.innerHTML;
        if(word == '取消关注'){
          this.$refs.followWord.innerHTML = '已关注';
          this.$refs.icon.className = 'fa fa-check';
          this.$refs.followWord2.innerHTML = '已关注';
          this.$refs.icon2.className = 'fa fa-check';
        }
      },
      islike:function(){

        if(!this.$refs.islikeshow.classList.contains('active')){
          this.$refs.islikeshow.classList.add('active');
          this.islikeCount = this.islikeCount + 1;
        } else {
          this.$refs.islikeshow.classList.remove('active');
          this.islikeCount = this.islikeCount - 1;
        }

      }
    }
  }
</script>

<style scoped>
    /*.more-share {*/
        /*position: relative;*/
        /*display: inline-block;*/
        /*border: 1px solid black;*/
    /*}*/

    /*.more-share .more-share-show {*/
        /*visibility: hidden;*/
        /*width: 120px;*/
        /*background-color: #eee;*/
        /*border: 1px solid #333;*/
        /*color: #333;*/
        /*text-align: center;*/
        /*border-radius: 6px;*/
        /*padding: 5px 0;*/
        /*position: absolute;*/
        /*z-index: 1;*/
        /*bottom: 60px;*/
        /*left: -10%;*/
    /*}*/
    /*.more-share .sanjiao{*/
        /*display: block;*/
        /*width: 10px;*/
        /*height: 10px;*/
        /*transform: rotate(45deg);*/
        /*left: 45%;*/
        /*!*bottom: 0px;*!*/
        /*position: absolute;*/
        /*background-color: #eee;*/
        /*border-bottom:1px solid #333 ;*/
        /*border-right:1px solid #333 ;*/
        /*!*border-top: 10px solid #eee;*!*/
        /*!*border-right: 10px solid #fff;*!*/
        /*!*border-left: 10px solid #fff;*!*/

    /*}*/

</style>