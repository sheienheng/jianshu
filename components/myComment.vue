<template>
    <div>
        <div class="comment-list" id="comment-list">
            <!--提交的留言表单-->
            <form class="new-comment">
                <nuxt-link class="avatar" to="/u/213">
                    <img src="../assets/img/default-avatar.jpg" alt="">
                </nuxt-link>
                <textarea placeholder="写下你的评论" @focus="send=true"
                v-model="value"></textarea>
                <transition :duration="300" name="fade">
                    <div v-if="send" class="write-function-block clearfix">
                        <div class="emoji-modal-wrap">
                            <a href="javascript:void(0)" class="emoji" @click="showEmoji=!showEmoji">
                                <i class="fa fa-smile-o"></i>
                            </a>
                            <transition :duration="1000" name="fade">
                                <div class="emoji-modal arrow-up" v-if="showEmoji">
                                    <vue-emoji @select="selectEmoji"></vue-emoji>
                                </div>
                            </transition>
                        </div>
                        <div class="hint">
                            Ctrl + Enter发表
                        </div>
                        <a href="javascript:void(0)" class="btn btn-send" @click="sendData">
                            发送
                        </a>
                        <a href="javascript:void(0)" class="cancel" @click="send=false">
                            取消
                        </a>
                    </div>
                </transition>

            </form>
            <!--留言的列表-->
            <div id="normal-comment-list" class="normal-comment-list">
                <!--留言的排序-->
                <div class="top-title">
                    <span>25条评论</span>
                    <a href="javascript:void(0)" class="author-only">
                        只看作者
                    </a>
                    <div class="pull-right">
                        <a href="javascript:void(0)" class="active">
                            按喜欢排序
                        </a>
                        <a href="javascript:void(0)">
                            按时间正序
                        </a>
                        <a href="javascript:void(0)">
                            按时间倒序
                        </a>
                    </div>
                </div>
                <!--留言的正文-->
                <div class="comment-placeholder" style="display: none">
                    <div class="author">
                        <div class="avatar"></div>
                        <div class="info">
                            <div class="name"></div>
                            <div class="meta"></div>
                        </div>
                    </div>
                    <div class="title"></div>
                    <div class="title animated-delay"></div>
                    <div class="tool-group">
                        <i class="fa fa-thumbs-o-up"></i>
                        <div class="zan"></div>
                        <i class="fa fa-comment-o"></i>
                        <div class="zan"></div>
                    </div>
                </div>
                <div class="comment" v-for="(comment,index) in comments"
                :id="'comment-'+comment.id">
                    <div class="comment-content">
                        <div class="author">
                            <!--<div class="v-tooltip-content">-->
                                <nuxt-link to="/u/123" class="avatar">
                                    <img :src="comment.user.avatar" alt="">
                                </nuxt-link>
                            <!--</div>-->
                            <div class="info">
                                <nuxt-link to="/u/123" class="name">
                                    {{comment.user.nick_name}}
                                </nuxt-link>
                                <div class="meta">
                                    <span>
                                        {{comment.floor}}楼.{{comment.create_at}}
                                    </span>
                                </div>
                            </div>
                        </div>
                        <!--正文部分-->
                        <div class="comment-wrap"></div>
                    </div>
                    <!--二级回复-->
                    <div class="sub-comment-list"></div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
  import vueEmoji from '~/components/vueEmoji'
  export default {
    name: 'myComment',
    data(){
      return{
        send:false,
        showEmoji:false,
        value:'',
        comments:[
          {
            id:20101998,
            floor:2,
            liked:true,
            likes_count:12,
            note_id:23354357,
            user_id:8475271,
            user:{
              avatar:'/default-avatar.jpg',
              id:8475271,
              is_author:false,
              nick_name:'我很拽',
              badge:null
            },
            create_at:'2018-01-29T22:30:58.000+08:00',
            children_count:4,
            complied_content:'静静地我在聆听，听到了诗人美妙的心声……好美！棒棒哒……喜欢！👍💝🌹🌹',
            children:[
              {
                id:20102151,
                user_id:8179167,
                complied_content:'啦啦啦啦啦。☕☕',
                user:{
                  id: 8179167,
                  nickname: "渴死之水"
                },
                parent_id: 20101998,
                created_at: "2018-01-29T22:27:22.000+08:00",
              }
            ]
          },
          {
            id:20147520,
            floor:3,
            liked:true,
            likes_count:15,
            note_id:23354357,
            user_id:10407888,
            user:{
              avatar:'http://upload.jianshu.io/users/upload_avatars/10407888/388ec803-b614-4dcf-91da-5892b9d71a1b.jpg',
              id:10407888,
              is_author:false,
              nick_name:'画皮流殇',
              badge:null
            },
            create_at:'2018-01-31T09:49:35.000+08:00',
            children_count:1,
            complied_content:'轻轻地走<br>飘过你的心间<br>轻触清风<br>留下一指忧伤<br>阳光普照<br>愿你微笑相映',
            children:[
              {
                id: 20147583,
                user_id:8179167,
                complied_content:'<a href="/users/cadca6980261" class="maleskine-author" target="_blank" data-user-slug="cadca6980261">@画皮流殇</a> 👍👍👍🌹🌹🌹',
                user:{
                  id: 8179167,
                  nickname: "渴死之水"
                },
                parent_id: 20147520,
                created_at: "2018-01-31T09:51:29.000+08:00",
              }
            ]
          },
          {
            id:20100836,
            floor:4,
            liked:true,
            likes_count:10,
            note_id:23354357,
            user_id:7839387,
            user:{
              avatar:'http://upload.jianshu.io/users/upload_avatars/7839387/d3dfd67e-8eef-4c63-9c1f-31663341a499.jpg',
              id:7839387,
              is_author:false,
              nick_name:'长亭外的夏小乔',
              badge:null
            },
            create_at:'2018-01-29T22:00:29.000+08:00',
            children_count:1,
            complied_content:'抢到沙发啦。☕☕',
            children:[
              {
                id: 20100917,
                user_id:8179167,
                complied_content:'<a href="/users/22d2f8f31588" class="maleskine-author" target="_blank" data-user-slug="22d2f8f31588">@长亭外的夏小乔</a> 🙏🙏🙏🍎🍎🌹🌹🌹',
                user:{
                  id: 8179167,
                  nickname: "渴死之水"
                },
                parent_id: 20100836,
                created_at: "2018-01-29T22:02:13.000+08:00",
              },
              {
                id: 20103918,
                user_id:7839387,
                complied_content:'<a href="/users/0371efd5f978" class="maleskine-author" target="_blank" data-user-slug="0371efd5f978">@渴死之水</a> 晚安，朋友，做个好梦。🌙✨✨✨✨✨',
                user:{
                  id: 7839387,
                  nickname: "长亭外的夏小乔"
                },
                parent_id: 20100836,
                created_at: "2018-01-29T23:11:40.000+08:00",
              },
              {
                id: 20104201,
                user_id:8179167,
                complied_content:'<a href="/users/22d2f8f31588" class="maleskine-author" target="_blank" data-user-slug="22d2f8f31588">@长亭外的夏小乔</a> 🙏🙏🙏🍎🍎🌹🌹🌹',
                user:{
                  id: 8179167,
                  nickname: "渴死之水"
                },
                parent_id: 20100836,
                created_at: "2018-01-29T23:19:39.000+08:00",
              },
            ]
          },
        ]
      }
    },
    components:{
      vueEmoji
    },
    methods:{
        selectEmoji:function(code){
            this.showEmoji = false;
            this.value += code;
        },
        sendData:function(){

        }
    }
  }
</script>

<style>
    .fade-enter-active,.fade-leave-active {
        opacity: 1;
        transition: .3s;
        -webkit-transition: .3s
    }
    .fade-enter,.fade-leave-to {
        opacity: 0;
        transform: translate3d(0,-5%,0);
        -webkit-transform: translate3d(0,-5%,0);
        transition: .3s;
        -webkit-transition: .3s
    }
    .note .post .comment-list{
        padding-top: 20px;
    }
    .note .post .comment-list .new-comment{
        position: relative;
        margin-left: 48px;
        margin-bottom: 20px;
    }
    .note .post .comment-list .avatar{
        width: 38px;
        height: 38px;
        display: inline-block;
        margin-right: 5px;
    }
    .note .post .comment-list .new-comment .avatar{
        position: absolute;
        left: -48px;
    }
    .note .post .comment-list .new-comment textarea{
        width: 100%;
        height: 80px;
        padding: 10px 15px;
        border: 1px solid #ccc;
        border-radius: 4px;
        display: inline-block;
        vertical-align: top;
        outline-style: none;
        resize: none;/*不能改变大小*/
        background-color: #f8f8f8;
        /*position: relative;*/
        /*z-index: 999;*/
    }
    .note .post .comment-list .new-comment .emoji{
        float: left;
        margin-top: 18px;
    }
    .note .post .comment-list .new-comment .emoji i{
        font-size: 25px;
        color: #969696;
    }
    .note .post .comment-list .new-comment .emoji i:hover{
        color: #333;
    }
    .note .post .comment-list .new-comment .hint{
        float: left;
        margin: 18px 0 0 10px;
        font-size: 13px;
        color: #969696;
    }
    .note .post .comment-list .new-comment .cancel{
        float: right;
        font-size: 16px;
        margin: 18px 30px 0 0;
        color: #969696!important;
    }
    .note .post .comment-list .new-comment .cancel:hover{
        color: #333!important;
    }
    .note .post .comment-list .new-comment .btn-send{
        float: right;
        width: 78px;
        padding: 8px 18px;
        margin: 10px 0;
        font-size: 18px;
        background-color: #42c02e;
        border-radius: 20px;
        color: #fff!important;
        text-align: center;
        box-shadow: none;
    }
    .note .post .comment-list .new-comment .btn-send:hover{
        background-color: #3db922;
    }
    .note .post .comment-list .new-comment .emoji-modal-wrap{
        position: relative;
    }
    .note .post .comment-list .new-comment .emoji-modal-wrap .emoji-modal{
        position: absolute;
        top:50px;
        left: -48px;
        width: 402px;
        height: 208px;
        padding: 10px;
        /*overflow: hidden;*/
        border: 1px solid #dcdcdc;
        border-radius: 4px;
        box-shadow: 0 5px 25px rgba(0,0,0,.2);
        background-color: #fff;
    }
    .arrow-up:after{
        content: '';
        display: inline-block;
        /*border-left: 9px solid rgba(238,238,238,0);*/
        /*border-right: 9px solid rgba(238,238,238,0);*/
        /*border-bottom: 9px solid rgb(238,238,238);*/
        position: absolute;
        left: 52px;
        top: -6px;
        width: 10px;
        height: 10px;
        border-left: 1px solid #d9d9d9;
        border-top: 1px solid #d9d9d9;
        /*border-bottom-color: #d9d9d9;*/
        transform: rotate(45deg);
        background-color: #fff;
    }
    .note .post .comment-list .normal-comment-list{
        margin-top: 30px;
    }
    .note .post .comment-list .normal-comment-list .top-title{
        padding-bottom: 20px;
        border-bottom: 1px solid #f0f0f0;
    }
    .note .post .comment-list .normal-comment-list .top-title span{
        font-size: 17px;
        font-weight: 700;
    }
    .note .post .comment-list .top-title .author-only{
        font-size: 12px;
        padding: 4px 8px;
        border: 1px solid #e1e1e1;
        border-radius: 12px;
        color: #969696!important;
        margin-left: 10px;
    }
    .note .post .comment-list .top-title .pull-right a{
        margin-left: 10px;
        font-size: 12px;
        color: #969696!important;
    }
    .note .post .comment-list .top-title .pull-right a.active{
        color: #2f2f2f!important;
    }
    .note .post .comment-list .comment{
        padding: 20px 0 30px 0;
        border: 1px solid #f0f0f0;

    }
    .note .post .comment-list .info{
        display: inline-block;
        vertical-align: middle;
    }
    .note .post .comment-list .info .name{
        font-size: 15px;
    }
    .note .post .comment-list .info .meta{
        font-size: 12px;
        color: #969696;
    }
</style>