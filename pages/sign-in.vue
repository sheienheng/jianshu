<template>
    <div class="sign">
        <!--logo-->
        <div class="logo">
            <nuxt-link to="/">
                <img src="~assets/img/logo.png">
            </nuxt-link>
        </div>
        <!--登录表单-->
        <div class="main">
            <div class="title">
                <h4>
                <nuxt-link class="active" to="/sign-in">登录</nuxt-link>
                <b>·</b>
                <nuxt-link to="/sign-out">注册</nuxt-link>
                </h4>
            </div>
            <div class="js-sign-in">
                <form method="post" >
                    <div class="input-prepend">
                        <input class="top-radius" type="text" value="" name="" placeholder="手机号或邮箱">
                        <i class="fa fa-user"></i>
                    </div>
                    <div class="input-prepend">
                        <input class="bottom-radius" type="text" value="" name="" placeholder="密码">
                        <i class="fa fa-lock"></i>
                    </div>
                    <div class="remember">
                        <input type="checkbox">&nbsp;
                        <span>记住我</span>
                    </div>
                    <div class="help">
                        <nuxt-link to="/help">
                            登录遇到问题?
                        </nuxt-link>
                    </div>
                    <input class="btn btn-primary" value="登录">
                </form>
                <div class="more-sign">
                    <p>社交账号登录</p>
                    <ul>
                        <li class="sign-weibo">
                            <a href="#">
                                <i class="fa fa-weibo" aria-hidden="true"></i>
                            </a>
                        </li>
                        <li class="sign-wechat">
                            <a href="#">
                                <i class="fa fa-wechat" aria-hidden="true"></i>
                            </a>
                        </li>
                        <li class="sign-qq">
                            <a href="#">
                                <i class="fa fa-qq" aria-hidden="true"></i>
                            </a>
                        </li>
                        <li class="another">
                            <a href="#">
                                其它
                            </a>
                        </li>
                    </ul>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
    import 'assets/css/sign.css'
    export default{
        layout:'sign',//当前页面所使用的默认模板是layouts文件夹下的sign.vue
        head () {
          return{
            title:"登录-简书",
            meta:[
              {hid: 'description',name:'description',content:'登录页面'}
            ]
          }
        }
    }
</script>
