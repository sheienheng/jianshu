<template>
    <div>
        <nav class="navbar navbar-default nav-fixed-top">
            <div class="width-limit">
                <!--logo-->
                <nuxt-link class="main-logo" to="/">
                    <img src="../assets/img/nav-logo.png">
                </nuxt-link>
                <!--写文章-->
                <nuxt-link class="write-btn btn" to="/creat">
                    <i class="fa fa-edit"></i>
                    写文章
                </nuxt-link>
                <!--登录注册按钮-->
                <!--<nuxt-link to="/sign-out" class="btn sign-out">注册</nuxt-link>-->
                <!--<nuxt-link to="/sign-in" class="btn sign-in">登录</nuxt-link>-->
                <!--如果用户登录显示头像-->
                <div class="user" style="" @mouseover='userShow = true' @mouseleave='userShow = false'>
                    <div class="drop-down">
                        <nuxt-link class="avatar" to="/users/myhomepage">
                            <img src="../assets/img/default-avatar.jpg" alt="">
                        </nuxt-link>
                    </div>
                    <div class="drop-menu" v-show="userShow">
                        <ul>
                            <li>
                                <nuxt-link to="/users/myhomepage">
                                    <i class="fa fa-home"></i>
                                    我的主页
                                </nuxt-link>
                            </li>
                            <li>
                                <nuxt-link to="/users/bookmarks">
                                    <i class="fa fa-bookmark"></i>
                                    收藏的文章
                                </nuxt-link>
                            </li>
                            <li>
                                <nuxt-link to="/users/likeBook">
                                    <i class="fa fa-heart"></i>
                                    喜欢的文章
                                </nuxt-link>
                            </li>
                            <li>
                                <nuxt-link to="/users/setting/basic">
                                    <i class="fa fa-cog"></i>
                                    设置
                                </nuxt-link>
                            </li>
                            <li>
                                <nuxt-link to="/">
                                    <i class="fa fa-sign-out"></i>
                                    退出
                                </nuxt-link>
                            </li>
                        </ul>
                    </div>
                </div>
                <div class="my-container">
                    <ul class="nav-list">
                        <li :class="headcount==0?'active':''">
                            <nuxt-link to="/">
                                <i class="fa fa-compass"></i>
                                <span>发现</span>
                            </nuxt-link>
                        </li>
                        <li :class="headcount==1?'active':''">
                            <nuxt-link to="/">
                                <i class="fa fa-book"></i>
                                <span>关注</span>
                            </nuxt-link>
                        </li>
                        <li class="notify" :class="headcount==2?'active':''" @mouseover='notifyShow = true' @mouseleave='notifyShow = false'>
                            <nuxt-link to="/notifications/comments">
                                <i class="fa fa-bell"></i>
                                <span>消息</span>
                            </nuxt-link>
                            <div class="drop-menu" v-show="notifyShow">
                                <ul>
                                    <li>
                                        <nuxt-link to="/notifications/comments">
                                            <i class="fa fa-comment-o"></i>
                                            评论
                                        </nuxt-link>
                                    </li>
                                    <li>
                                        <nuxt-link to="/notifications/chats">
                                            <i class="fa fa-envelope-open-o"></i>
                                            简信
                                        </nuxt-link>
                                    </li>
                                    <li>
                                        <nuxt-link to="/notifications/requests">
                                            <i class="fa fa-upload"></i>
                                            投稿请求
                                        </nuxt-link>
                                    </li>
                                    <li>
                                        <nuxt-link to="/notifications/likes">
                                            <i class="fa fa-heart-o"></i>
                                            喜欢和赞
                                        </nuxt-link>
                                    </li>
                                    <li>
                                        <nuxt-link to="/notifications/follows">
                                            <i class="fa fa-user-o"></i>
                                            关注
                                        </nuxt-link>
                                    </li>
                                </ul>
                            </div>
                        </li>
                        <li class="search">
                            <form action="" method="post">
                                <input type="text" placeholder="搜索" @focus="bgShow=true" @blur="bgShow=false">
                                <nuxt-link to="/search" class="search-button" :class="{active:bgShow}">
                                    <i class="fa fa-search"></i>
                                </nuxt-link>
                            </form>
                        </li>
                    </ul>
                </div>
            </div>
        </nav>
    </div>
</template>
<script>
    export default{
      name:'myHeader', //给组件命名
      data(){
        return{
          userShow:false,
          notifyShow:false,
          bgShow:false,
          headCount:-1,
        }
      },
      props:['headcount'],
      mounted(){
        this.ss()
      },
      methods:{
        ss:function () {
          console.log(this.headcount)
        }
      }
    }
</script>
<!--scoped 只在当前组件使用css样式-->
<style scoped>
    nav{
        height: 56px;
        width: 100%;
    }
     nav.navbar{
        padding: 0;
        border-bottom: 1px solid #dcdcdc;
        margin-bottom: 20px;
        background-color: #fff;
    }
    nav.nav-fixed-top{
        position: fixed;
        top: 0;
        left: 0;
        z-index: 999;
    }
    nav .width-limit{
        min-width: 768px;
        width: 1440px;
        margin: 0 auto;
    }
    nav .main-logo{
        float: left;
        height: 56px;
        padding: 0;
    }
    nav .main-logo img{
        height: 100%;
    }
    nav .write-btn{
        float: right;
        background-color: #ea6f5a;
        line-height: 24px;
        margin-top: 6px;
        color: #fff!important;
        border-radius: 20px;
        font-size: 16px;
    }
    nav .user{
        float: right;
        position: relative;
    }
    nav .user .avatar{
        position: relative;
        margin:8px 28px 8px 20px;
        width: 40px;
        height: 40px;
        display: block;
        border: 1px solid #ccc;
        border-radius: 50%;
    }
    nav .user .avatar:after{
        content: "";
        position: absolute;
        top: 18px;
        right: -14px;
        border-left: 5px solid transparent;
        border-right: 5px solid transparent;
        border-top: 6px solid #999;
    }
    nav .user:hover{
        background-color: #f5f5f5;
    }
    nav .user .avatar img{
        width: 100%;
        height: 100%;
        border-radius: 50%;
    }
    nav .user .drop-menu{
        position: absolute;
        left: 0;
        min-width: 160px;
        box-shadow: 0 0 8px rgba(0,0,0,.1);
        background-color: #fff;
    }
    nav .user .drop-menu ul{
        border: 1px solid #ccc;
        padding: 10px 0;
        margin:0;
    }
    nav .user .drop-menu ul li a{
        padding: 10px 20px;
        display: block;
        /*color: #333;*/
    }
    nav .user .drop-menu ul li a:hover{
        background-color: #f5f5f5;
    }
    nav .user .drop-menu ul li i{
        margin-right: 15px;
        color: #ea6f5a;
        font-size: 18px;
    }
    nav .nav-list{
        margin: 0 -15px!important;
        padding: 0;
    }
    nav .nav-list:after{
        /*float: left;*/
        content: '';
        height: 0;
        display: block;
        visibility: hidden;
        clear: both;
    }
    nav .nav-list>li{
        float: left;
        /*margin-right: 5px;*/
    }
    nav .nav-list>li:hover{
        background-color: #f5f5f5;
    }
    nav .nav-list>li>a{
        display: block;
        height: 55px;
        padding: 15px;
        /*line-height: 56px;*/
        margin-right: 10px;
        font-size: 18px;
    }
    nav .nav-list>li a i{
        margin-right: 7px;
        font-size: 20px;
        margin-top: 5px;
    }
    nav .nav-list>li.active{
        color: #ea6f5a;
        background-color: #fff;
    }
    nav .nav-list>li.active .drop-menu a{
        color: #333!important;
    }
    nav .nav-list .notify{
        position: relative;
    }
    nav .nav-list .notify .drop-menu{
        position: absolute;
        left: 0;
        top: 56px;
        min-width: 160px;
        box-shadow: 0 0 8px rgba(0,0,0,.1);
        font-size: 15px;
        background-color: #fff;
    }
    nav .nav-list .notify .drop-menu ul{
        border: 1px solid #ccc;
        padding: 10px 0;
        margin:0;
    }
    nav .nav-list .notify .drop-menu ul li a{
        padding: 10px 20px;
        margin: 0;
        display: block;
    }
    nav .nav-list .notify .drop-menu ul li a:hover{
        background-color: #f5f5f5;
    }
    nav .nav-list .notify .drop-menu ul li i{
        margin-right: 15px;
        color: #ea6f5a;
        font-size: 18px;
    }
    nav a.sign-in{
        float: right;
        width: 80px;
        height: 40px;
        margin: 7px 6px 0 7px;
        line-height: 24px;
        font-size: 15px;
    }
    nav a.sign-out:hover{
        background-color: #c8c8c8;
    }
    nav a.sign-out:active{
        box-shadow: none;
    }
    nav a.sign-out{
        float: right;
        width: 80px;
        height: 40px;
        margin: 7px 6px 0 7px;
        border: 1px solid #ea6f5a;
        border-radius: 15px;
        color: #ea6f5a!important;
        line-height: 24px;
        font-size: 15px;
    }
    nav .nav-list .search{
        padding-left: 15px;
    }
    nav .nav-list .search:hover{
        background-color: #fff;
    }
    nav .nav-list .search form{
        margin-top: 9px;
        position: relative;
    }
    nav .nav-list .search form input{
        width: 200px;
        height: 38px;
        border: none;
        background-color: rgba(238,238,238,.5);
        border-radius: 20px;
        padding: 0 30px 0 20px;
        font-size: 15px;
        transition: width .3s ease-in;
    }
    nav .nav-list .search form input:focus{
        width: 300px;
    }
    nav .nav-list .search .search-button{

    }
    nav .nav-list .search form a.search-button {
        display: block;
        width: 30px;
        height: 30px;
        position: absolute;
        right: 0;
        top: 2px;
        text-align: center;
    }
    nav .nav-list .search form a.active{
        background-color: #c8c8c8;
        border-radius: 50%;
    }

    @media (max-width: 768px) {
        nav .nav-list{
            display: none;
        }
    }
    @media (max-width: 1440px) {
        nav .nav-list>li>a i{
            display: none;
        }
        nav .nav-list .search form input{
            width: 160px;
        }
        nav .nav-list .search form input:focus{
            width: 240px;
        }
    }
    @media (max-width: 1080px) {
        nav .nav-list>li>a i{
            display: block;
        }
        nav .nav-list>li>a span{
            display: none;
        }
        nav .nav-list .search form input{
            width: 150px;
        }
        nav .nav-list .search form input:focus{
            width: 150px;
        }
    }

</style>