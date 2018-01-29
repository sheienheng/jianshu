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
                    <nuxt-link to="/sign-in">登录</nuxt-link>
                    <b>·</b>
                    <nuxt-link class="active" to="/sign-up">注册</nuxt-link>
                </h4>
            </div>
            <div class="js-sign-in">
                <form method="post" >
                    <div class="input-prepend">
                        <input class="top-radius" type="text" value="" name="" placeholder="手机号或邮箱">
                        <i class="fa fa-user"></i>
                    </div>
                    <div class="input-prepend">
                        <input type="text" value="" name="" placeholder="手机号">
                        <i class="fa fa-mobile" aria-hidden="true"></i>
                    </div>
                    <div class="input-prepend ssm">
                        <input type="text" name="" value="" placeholder="手机验证码">
                        <i class="fa fa-shield"></i>
                        <a class="send-ssm btn btn-sm btn-success">发送验证码</a>
                    </div>
                    <div class="input-prepend">
                        <input class="bottom-radius" type="text" value="" name="" placeholder="设置密码">
                        <i class="fa fa-lock"></i>
                    </div>
                    <input  class="btn btn-success sign-up-btn" value="注册" >
                    <p class="sign-up-msg">点击 “注册” 即表示您同意并愿意遵守简书<br>
                        用户协议 和 隐私政策 。</p>

                </form>
                <div class="more-sign">
                    <p>社交账号直接注册</p>
                    <ul>
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
        title:"注册-简书",
        meta:[
          {hid: 'description',name:'description',content:'注册页面'}
        ]
      }
    }
  }
</script>
