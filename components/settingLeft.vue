<template>
    <div>
        <ul id="noti">
            <li v-for="(f,index) in mes">
                <nuxt-link :to="toLink[index]" class="active"  v-if="index==data">
                    <span class="iconStyle">
                        <i :class="faClass[index]"></i>
                    </span>
                    {{f}}
                </nuxt-link>
                <nuxt-link :to="toLink[index]" v-if="index!=data">
                    <span class="iconStyle">
                        <i :class="faClass[index]"></i>
                    </span>

                    {{f}}
                </nuxt-link>
            </li>
        </ul>
    </div>
</template>

<script>
  export default {
    name: 'setting-left',
    props:['data'],
    data(){
      return{
        mes:['基础设置','个人资料','微博认证','黑名单','赞赏设置','账号管理'],
        activeChange:[
          {active:false},
          {active:false},
          {active:false},
          {active:false},
          {active:false},
          {active:false},
        ],
        toLink:[
          '/users/setting/basic',
          '/users/setting/profile',
          '/users/setting/weibo-auth',
          '/users/setting/blacklist',
          '/users/setting/reward-setting',
          '/users/setting/misc',
        ],
        faClass:[
          'fa fa-comment-o',
          'fa fa-envelope-open-o',
          'fa fa-upload',
          'fa fa-heart-o',
          'fa fa-user-o',
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
    ul#noti li .iconStyle{
        display: inline-block;
        width: 32px;
        height: 32px;
        border-radius: 2px;
        background-color: #969696;
        text-align: center;
        margin-right: 15px;
    }
    ul#noti li i{
        color: #fff;
        font-size: 18px;
    }
</style>