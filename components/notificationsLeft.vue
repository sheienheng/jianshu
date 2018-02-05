<template>
    <div>
        <ul id="noti">
            <li v-for="(f,index) in mes">
                <nuxt-link :to="toLink[index]" class="active"  v-if="index==data">
                    <i :class="faClass[index]"></i>
                    {{f}}
                </nuxt-link>
                <nuxt-link :to="toLink[index]" v-if="index!=data">
                    <i :class="faClass[index]"></i>
                    {{f}}
                </nuxt-link>
            </li>
        </ul>
    </div>
</template>

<script>
  export default {
    name: 'notifications-left',
    props:['data'],
    data(){
      return{
        mes:['评论','简信','投稿请求','喜欢和赞','关注'],
        activeChange:[
          {active:false},
          {active:false},
          {active:false},
          {active:false},
          {active:false},
        ],
        toLink:[
          '/notifications/comments',
          '/notifications/chats',
          '/notifications/requests',
          '/notifications/likes',
          '/notifications/follows',
        ],
        faClass:[
          'fa fa-comment-o',
          'fa fa-envelope-open-o',
          'fa fa-upload',
          'fa fa-heart-o',
          'fa fa-user-o',
        ]
      }
    },
  }
</script>

<style scoped>
    ul#noti li{
        line-height: 30px!important;
        font-size: 15px;
    }
    ul#noti li a.active{
        background-color: #f0f0f0;
    }
    ul#noti li a{
        padding: 10px 20px;
        display: block;
        border-radius: 4px;
    }
    ul#noti li a:hover{
        background-color: #f0f0f0;
        border-radius: 4px;
    }
    ul#noti li i{
        margin-right: 15px;
        color: #ea6f5a;
        font-size: 18px;
    }
</style>