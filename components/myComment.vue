<template>
    <div>
        <div class="comment-list" id="comment-list">
            <!--提交的留言表单-->
            <form class="new-comment">
                <nuxt-link class="avatar" to="/u/213">
                    <img src="../assets/img/default-avatar.jpg" alt="">
                </nuxt-link>
                <textarea placeholder="写下你的评论" @focus="send=true"
                          v-model="valueone" v-focus="valueonefocus"
                          @blur="valueonefocus=false"></textarea>
                <transition :duration="300" name="fade">
                    <div v-if="send" class="write-function-block clearfix">
                        <div class="emoji-modal-wrap">
                            <a href="javascript:void(0)" class="emoji" @click="showEmoji=!showEmoji">
                                <i class="fa fa-smile-o"></i>
                            </a>
                            <transition :duration="1000" name="fade">
                                <div class="emoji-modal arrow-up" v-if="showEmoji" @click="selcount(-1)">
                                    <vue-emoji @select="selectEmoji"></vue-emoji>
                                </div>
                            </transition>
                        </div>
                        <div class="hint">
                            Ctrl + Enter发表
                        </div>
                        <a href="javascript:void(0)" class="btn btn-send">
                            发送
                        </a>
                        <a href="javascript:void(0)" class="cancel" @click="
                        send=false;valueone='';showEmoji = false">
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
                    <a href="javascript:void(0)" class=" author-only">
                        只看作者
                    </a>
                    <div class="pull-right">
                        <a href="javascript:void(0)" ref="sortlike" class="active" @click="sortchange(0)">
                            按喜欢排序
                        </a>
                        <a href="javascript:void(0)" ref="sorttime1" @click="sortchange(1)">
                            按时间正序
                        </a>
                        <a href="javascript:void(0)" ref="sorttime0" @click="sortchange(2)">
                            按时间倒序
                        </a>
                    </div>
                </div>
                <!--留言的正文-->
                <div class="comment-placeholder" style="display: none;">
                    <div class="author">
                        <div class="avatar" style="vertical-align: middle;"></div>
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
                            <div class="avatar" :id="'img-'+ index">
                                <nuxt-link to="/u/123">
                                    <img :src="comment.user.avatar" alt="">
                                </nuxt-link>
                            </div>
                            <div class="info">
                                <nuxt-link to="/u/123" class="name">
                                    {{comment.user.nick_name}}
                                </nuxt-link>
                                <div class="meta">
                                    <span>
                                        {{comment.floor}}楼.{{comment.create_at|formatDate}}
                                    </span>
                                </div>
                            </div>
                        </div>
                        <!--正文部分-->
                        <div class="comment-wrap">
                            <p v-html="comment.complied_content"></p>
                            <div class="tool-group">
                                <a href="javascript:void(0)" @click="zan(index)" class="like-bottom zan-animation">
                                    <i :class="comment.liked?'fa fa-thumbs-up':'fa fa-thumbs-o-up'" ></i>
                                    <span :class="comment.liked? 'reallike':''">{{comment.likes_count}}人点赞</span>
                                </a>
                                <a href="javascript:void(0)">
                                    <i class="fa fa-comment-o"></i>
                                    <span @click="huifu(index,'','top')">回复</span>
                                </a>
                            </div>
                        </div>
                    </div>
                    <!--二级回复-->
                    <div class="sub-comment-list">
                        <div v-for="(subComment,index2) in comment.children" :id="'comment-'+subComment.id"
                             class="sub-comment" v-if="comment.children.length != 0">
                            <p>
                                <nuxt-link to="/u/123">
                                    {{subComment.user.nickname}}
                                </nuxt-link>
                                :
                                <span v-html="subComment.complied_content">
                                    <!--{{subComment.complied_content}}-->
                                </span>
                            </p>
                            <div class="sub-tool-group">
                                <span>{{subComment.created_at | formatDate}}</span>
                                <a href="javascript:void(0)">
                                    <i class="fa fa-comment-o"></i>
                                    <span @click="huifu(index,subComment.user.nickname,subComment.id)">回复</span>
                                </a>
                            </div>
                        </div>
                        <div class="more-comment">
                            <a href="javascript:void(0)" class="add-commnet-btn" @click="huifu(index,'','bottom')"
                               v-if="comment.children.length != 0">
                                <i class="fa fa-pencil"></i>
                                <span>添加新评论</span>
                            </a>
                            <transition :duration="500" name="fade">
                                <div class="clearfix" v-if="showPings.includes(index)">
                                    <div>
                                        <textarea placeholder="写下你的评论" v-model="valuem[index].value"
                                                  @blur="focusStatus[index]=false"
                                                  v-focus="focusStatus[index]"></textarea>
                                        <a href="javascript:void(0)" class="emoji" @click="smilebtn(index)">
                                            <i class="fa fa-smile-o"></i>
                                        </a>
                                        <div class="emoji-modal-wrap">
                                            <transition :duration="1000" name="fade">
                                                <div v-if="smiles[index].smile" class="emoji-modal arrow-up"
                                                     @click="selcount(index)">
                                                    <vue-emoji @select="selectEmoji"></vue-emoji>
                                                </div>
                                            </transition>
                                            <div class="hint">
                                                Ctrl + Enter发表
                                            </div>
                                            <a href="javascript:void(0)" class="btn btn-send">
                                                发送
                                            </a>
                                            <a href="javascript:void(0)" class="cancel" @click="huifu2(index)">
                                                取消
                                            </a>
                                        </div>
                                    </div>
                                </div>
                            </transition>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <span style="display: none">{{dddd}}</span>
    </div>
</template>

<script>
  import vueEmoji from '~/components/vueEmoji'

  export default {
    name: 'myComment',
    data () {
      return {
        send: false,
        showEmoji: false,
        valueone: '',
        valueonefocus:false,
        value: '',
        focusStatus:[],
        valuem: [],
        showPings: [],
        smiles: [],
        comments: [
          {
            id: 20101998,
            floor: 2,
            liked: true,
            likes_count: 12,
            note_id: 23354357,
            user_id: 8475271,
            user: {
              avatar: '/default-avatar.jpg',
              id: 8475271,
              is_author: false,
              nick_name: '我很拽',
              badge: null
            },
            create_at: '2018-01-29T22:30:58.000+08:00',
            children_count: 4,
            complied_content: '静静地我在聆听，听到了诗人美妙的心声……好美！棒棒哒……喜欢！👍💝🌹🌹',
            children: [
              {
                id: 20102151,
                user_id: 8179167,
                complied_content: '啦啦啦啦啦。☕☕',
                user: {
                  id: 8179167,
                  nickname: '渴死之水'
                },
                parent_id: 20101998,
                created_at: '2018-01-29T22:27:22.000+08:00',
              }
            ]
          },
          {
            id: 20147520,
            floor: 3,
            liked: true,
            likes_count: 15,
            note_id: 23354357,
            user_id: 10407888,
            user: {
              avatar: 'http://upload.jianshu.io/users/upload_avatars/10407888/388ec803-b614-4dcf-91da-5892b9d71a1b.jpg',
              id: 10407888,
              is_author: false,
              nick_name: '画皮流殇',
              badge: null
            },
            create_at: '2018-01-31T09:49:35.000+08:00',
            children_count: 1,
            complied_content: '轻轻地走<br>飘过你的心间<br>轻触清风<br>留下一指忧伤<br>阳光普照<br>愿你微笑相映',
            children: [
              {
                id: 20147583,
                user_id: 8179167,
                complied_content: '<a href="javascript:void(0)">@画皮流殇</a> 👍👍👍🌹🌹🌹',
                user: {
                  id: 8179167,
                  nickname: '渴死之水'
                },
                parent_id: 20147520,
                created_at: '2018-01-31T09:51:29.000+08:00',
              }
            ]
          },
          {
            id: 20100836,
            floor: 4,
            liked: false,
            likes_count: 10,
            note_id: 23354357,
            user_id: 7839387,
            user: {
              avatar: 'http://upload.jianshu.io/users/upload_avatars/7839387/d3dfd67e-8eef-4c63-9c1f-31663341a499.jpg',
              id: 7839387,
              is_author: false,
              nick_name: '长亭外的夏小乔',
              badge: null
            },
            create_at: '2018-01-29T22:00:29.000+08:00',
            children_count: 1,
            complied_content: '抢到沙发啦。☕☕',
            children: [
              {
                id: 20100917,
                user_id: 8179167,
                complied_content: '<a href="/users/22d2f8f31588" class="maleskine-author" target="_blank" data-user-slug="22d2f8f31588">@长亭外的夏小乔</a> 🙏🙏🙏🍎🍎🌹🌹🌹',
                user: {
                  id: 8179167,
                  nickname: '渴死之水'
                },
                parent_id: 20100836,
                created_at: '2018-01-29T22:02:13.000+08:00',
              },
              {
                id: 20103918,
                user_id: 7839387,
                complied_content: '<a href="/users/0371efd5f978" class="maleskine-author" target="_blank" data-user-slug="0371efd5f978">@渴死之水</a> 晚安，朋友，做个好梦。🌙✨✨✨✨✨',
                user: {
                  id: 7839387,
                  nickname: '长亭外的夏小乔'
                },
                parent_id: 20100836,
                created_at: '2018-01-29T23:11:40.000+08:00',
              },
              {
                id: 20104201,
                user_id: 8179167,
                complied_content: '<a href="/users/22d2f8f31588" class="maleskine-author" target="_blank" data-user-slug="22d2f8f31588">@长亭外的夏小乔</a> 🙏🙏🙏🍎🍎🌹🌹🌹',
                user: {
                  id: 8179167,
                  nickname: '渴死之水'
                },
                parent_id: 20100836,
                created_at: '2018-01-29T23:19:39.000+08:00',
              },
            ]
          },
          {
            id: 201019966,
            floor: 2,
            liked: false,
            likes_count: 0,
            note_id: 23354357,
            user_id: 8475271,
            user: {
              avatar: '/default-avatar.jpg',
              id: 8475271,
              is_author: false,
              nick_name: 'biubiu',
              badge: null
            },
            create_at: '2018-01-29T22:30:59.000+08:00',
            children_count: 0,
            complied_content: '棒棒哒……喜欢！👍💝🌹🌹',
            children: []
          },
        ],
        dddd:'q',
        showPop2: false,
        changemes: [],
        changeIndex:-1,
        colorchange: [],
        timearr:[],
        lastEmojisIndex:0,
        commentFormState:[],
      }
    },
    created () {
      this.pushMore
    },
    components: {
      vueEmoji
    },
    methods: {
      selectEmoji: function (code) {
        this.showEmoji = false
        this.value += code
      },
      selcount: function (index) {
        if (index < 0) {
          this.valueone = this.value
          this.valueonefocus=true
          this.value = ''
        } else {
          this.valuem[index].value += this.value
          this.value = ''
          this.smiles[index].smile = false
        }
        this.focusStatus[index] = true
        this.smilesfalse();
      },
      smilesfalse:function(){
        for(let i in this.comments){
          this.smiles[i].smile = false;
        }
      },
      smilebtn: function (index) {
        this.smiles[index].smile = !this.smiles[index].smile
      },
      huifu: function (index,mes,id) {
        if (this.changemes[index] == id) {
          this.showPings.splice(this.showPings.indexOf(index),1)
          this.changemes[index] = ''
        } else {
          if(!this.showPings.includes(index)){
            this.showPings.push(index);
          }
          this.changemes[index] = id;
        }
        if (mes) {
          this.valuem[index].value = '@ ' + mes + ' '
        } else {
          this.valuem[index].value = ''
        }
        this.focusStatus[index]= true;
        this.smilesfalse();
      },
      huifu2: function (index) {
        let value = this.showPings.indexOf(index)
        this.showPings.splice(value,1)
        this.valuem[index].value = '';
        this.changemes[index]=''
        this.smilesfalse();
      },
      zan: function (index) {
        if (this.comments[index].liked) {
          --this.comments[index].likes_count
          this.comments[index].liked=false
        //  点赞ajax的借口
        } else {
          this.comments[index].liked=true
          ++this.comments[index].likes_count
        }
      },
      likechange: function () {
        this.dddd='w';
        let item;
        for (let i in this.comments) {
          for (let j in this.comments) {
            if (j < this.comments.length) {
              if (this.comments[j].likes_count < this.comments[i].likes_count) {
                item = this.comments[j]
                this.comments[j] = this.comments[i]
                this.comments[i] = item;
              }
            }
          }
        }
      },
      timechange: function (index) {
        let item;
        for (let i in this.comments) {
          for (let j in this.comments) {
            if (j < this.comments.length) {
              if(index == 1){
                this.dddd='e';
                if (this.comments[j].create_at > this.comments[i].create_at) {
                  item = this.comments[j]
                  this.comments[j] = this.comments[i]
                  this.comments[i] = item;
                }
              }else{
                this.dddd='f';
                if (this.comments[j].create_at < this.comments[i].create_at) {
                  item = this.comments[j]
                  this.comments[j] = this.comments[i]
                  this.comments[i] = item;
                }
              }
            }
          }
        }
      },
      sortchange: function (index) {
        if (index == 0) {
          this.$refs.sortlike.className = 'active';
          this.$refs.sorttime0.className = '';
          this.$refs.sorttime1.className = '';
          this.likechange()
        }
        if (index == 1) {
          this.$refs.sortlike.className = '';
          this.$refs.sorttime0.className = '';
          this.$refs.sorttime1.className = 'active';
          this.timechange(1);
        }
        if (index == 2) {
          this.$refs.sortlike.className = '';
          this.$refs.sorttime0.className = 'active'
          this.$refs.sorttime1.className = '';
          this.timechange(0);
        }
      },
    },
    computed: {
      pushMore: function () {
        for (let i in this.comments) {
          this.valuem.push({value: ''})
          this.smiles.push({smile: false})
        }
        this.likechange();
      },
    },
    directives: {
      "focus": {
        // 钩子函数：bind inserted update componentUpdated unbind
        // 钩子函数的参数：el，binding，vnode，oldVnode
        // bind:function(el,binding,vnode,oldVnode){
        //   el.focus();
        // },
        update:function(el,{value}){
          if(value){
            el.focus()
          }
        },
        inserted: function (el,{value}) {
          // 聚焦元素
          if(value){
            el.focus()
          }
        }
      }
    },
  }
</script>

<style>
    .note .post .comment-list .comment .tool-group a.colorchange {
        color: red !important;
    }

    .fade-enter-active, .fade-leave-active {
        opacity: 1;
        transition: .3s;
        -webkit-transition: .3s
    }

    .fade-enter, .fade-leave-to {
        opacity: 0;
        transform: translate3d(0, -5%, 0);
        -webkit-transform: translate3d(0, -5%, 0);
        transition: .3s;
        -webkit-transition: .3s
    }

    .note .post .comment-list {
        padding-top: 20px;
    }

    .note .post .comment-list .new-comment {
        position: relative;
        margin-left: 48px;
        margin-bottom: 20px;
        padding: 5px 0;
    }

    .note .post .comment-list .avatar {
        width: 38px;
        height: 38px;
        display: inline-block;
        margin-right: 5px;
    }

    .note .post .comment-list .new-comment .avatar {
        position: absolute;
        left: -48px;
    }

    .note .post .comment-list textarea {
        width: 100%;
        height: 80px;
        padding: 10px 15px;
        border: 1px solid #ccc;
        border-radius: 4px;
        display: inline-block;
        vertical-align: top;
        outline-style: none;
        resize: none; /*不能改变大小*/
        background-color: #f8f8f8;
        /*position: relative;*/
        /*z-index: 999;*/
    }

    .note .post .comment-list .emoji {
        float: left;
        margin-top: 18px;
    }

    .note .post .comment-list .emoji i {
        font-size: 25px;
        color: #969696;
    }

    .note .post .comment-list .emoji i:hover {
        color: #333;
    }

    .note .post .comment-list .hint {
        float: left;
        margin: 18px 0 0 10px;
        font-size: 13px;
        color: #969696;
    }

    .note .post .comment-list .cancel {
        float: right;
        font-size: 16px;
        margin: 18px 30px 0 0;
        color: #969696 !important;
    }

    .note .post .comment-list .cancel:hover {
        color: #333 !important;
    }

    .note .post .comment-list .btn-send {
        float: right;
        width: 78px;
        padding: 8px 18px;
        margin: 10px 0;
        font-size: 18px;
        background-color: #42c02e;
        border-radius: 20px;
        color: #fff !important;
        text-align: center;
        box-shadow: none;
    }

    .note .post .comment-list .btn-send:hover {
        background-color: #3db922;
    }

    .note .post .comment-list .emoji-modal-wrap {
        position: relative;
    }

    .note .post .comment-list .emoji-modal-wrap .emoji-modal {
        position: absolute;
        top: 50px;
        left: -48px;
        width: 402px;
        height: 208px;
        padding: 10px;
        /*overflow: hidden;*/
        border: 1px solid #dcdcdc;
        border-radius: 4px;
        box-shadow: 0 5px 25px rgba(0, 0, 0, .2);
        background-color: #fff;
    }

    .arrow-up:after {
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

    .note .post .comment-list .normal-comment-list {
        margin-top: 30px;
    }

    .note .post .comment-list .normal-comment-list .top-title {
        padding-bottom: 20px;
        border-bottom: 1px solid #f0f0f0;
    }

    .note .post .comment-list .normal-comment-list .top-title span {
        font-size: 17px;
        font-weight: 700;
    }

    .note .post .comment-list .top-title .author-only {
        font-size: 12px;
        padding: 4px 8px;
        border: 1px solid #e1e1e1;
        border-radius: 12px;
        color: #969696 !important;
        margin-left: 10px;
    }

    .note .post .comment-list .top-title .pull-right a {
        margin-left: 10px;
        font-size: 12px;
        color: #969696 !important;
    }

    .note .post .comment-list .top-title .pull-right a.active {
        color: #2f2f2f !important;
    }

    .note .post .comment-list .comment {
        padding: 20px 0 30px 0;
        border-top: 1px solid #f0f0f0;
    }

    .note .post .comment-list .comment .comment-content .author {
        margin-bottom: 20px;
    }

    .note .post .comment-list .info {
        display: inline-block;
        vertical-align: middle;
    }

    .note .post .comment-list .info .name {
        font-size: 15px;
    }

    .note .post .comment-list .info .meta {
        font-size: 12px;
        color: #969696;
    }

    .note .post .comment-list .comment p {
        font-size: 16px;
        margin: 10px 0;
        line-height: 1.5;
        word-break: break-word !important;
    }

    .note .post .comment-list .comment .tool-group a {
        color: #969696 !important;
        margin-right: 10px;
    }
    .note .post .comment-list .comment .tool-group a:first-child:hover i{
        color: #ea6f5a;
    }
    .note .post .comment-list .comment .tool-group a:last-child:hover i{
        color: #333;
    }
    .note .post .comment-list .comment .tool-group a i {
        font-size: 18px;
        margin-right: 5px;
    }
    .note .post .comment-list .comment .tool-group a:hover span{
        color: #333;
    }
    .note .post .comment-list .comment .tool-group a i.fa-thumbs-up{
        color: #ea6f5a;
    }
    .note .post .comment-list .comment .tool-group a .reallike{
        color: #333;
    }
    .note .post .comment-list .comment .tool-group span {
        font-size: 14px;
    }

    .note .post .comment-list .sub-comment-list {
        border-left: 2px solid #d9d9d9;
        margin-top: 10px;
        padding: 0 20px;
    }

    .note .post .comment-list .sub-comment-list .sub-comment {
        padding-bottom: 15px;
        margin-bottom: 15px;
        border-bottom: 1px sol #f0f0f0;
    }

    .note .post .comment-list .sub-comment-list .sub-comment p {
        font-size: 14px;
        line-height: 1.5;
        margin-bottom: 5px;
    }

    .note .post .sub-comment-list .sub-comment p a {
        color: #3194d0 !important;
    }

    .note .post .comment-list .sub-tool-group {
        font-size: 12px;
        color: #969696;
    }

    .note .post .comment-list .sub-tool-group a {
        margin-left: 10px;
    }
    .note .post .comment-list .sub-tool-group a:hover span,
    .note .post .comment-list .sub-tool-group a:hover i{
        color: #333;
    }
    .note .post .comment-list .sub-tool-group a i {
        margin-right: 5px;
    }

    .note .post .comment-list .more-comment {
        font-size: 14px;
        color: #969696;
    }

    .note .post .comment-list .more-comment i {
        margin-right: 5px;
    }

    .note .post .comment-list .more-comment a:hover {
        color: #333 !important;
    }

    .popover {
        max-width: 500px;
        /*top: -3px!important;*/
        left: 6px !important;
    }

    .popover .popover-body .intro {
        width: 500px;
        display: flex;
    }

    .popover .popover-body .intro .introImg {
        width: 20%;
        padding: 15px;
    }

    .popover .popover-body .intro .avatar {
        /*display: inline-block;*/
        width: 70px;
        height: 70px;
    }

    .popover .popover-body .intro > .info {
        /*display: inline-block;*/
        padding: 10px 0;
    }

    .popover .popover-body .intro > .info > .name {
        font-size: 25px;
        font-weight: 700;
        line-height: 40px;
    }

    .popover .popover-body .intro > .info p {
        margin: 5px 0 0 0;
    }

    .popover .popover-body .intro > .info p.introLike {
        color: #969696;
    }

    .popover .popover-body .introMes {
        display: flex;
    }

    .popover .popover-body .introMes ul {
        width: 50%;
        display: flex;
        padding: 0 30px !important;
        justify-content: space-around;
    }

    .popover .popover-body .introMes ul li {
        font-size: 16px;
    }

    .popover .popover-body .introMes ul li span {
        font-size: 18px;
        font-weight: 700;
    }

    .popover .popover-body .introMes ul li p {
        color: #969696;
    }
</style>