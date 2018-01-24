<template>
    <div class="sign">
        <div class="logo">
            <nuxt-link to="/">
                <img src="../assets/img/loginLogo.png" alt="">
            </nuxt-link>
        </div>
        <!--登录的表单-->
        <div class="main">
            <div class="title">
                <h4>
                    <nuxt-link to="sign-in">登录</nuxt-link>
                    <b>.</b>
                    <nuxt-link to="sign-out" class="active">注册</nuxt-link>
                </h4>
            </div>
            <div class="js-form">
                <form action="/sign-out" method="post">
                    <div class="input-prepend">
                        <i class="fa fa-user"></i>
                        <input type="text" value="" name="" placeholder="你的昵称" class="top-radius">
                    </div>
                    <div class="input-prepend">
                        <i class="fa fa-mobile-phone"></i>
                        <input type="text" value="" name="" placeholder="手机">
                    </div>
                    <div class="input-prepend ssm">
                        <i class="fa fa-shield"></i>
                        <input type="text" value="" name="" placeholder="验证码">
                        <a href="#" class="send-ssm btn btn-success ">发送验证码</a>
                    </div>
                    <div class="input-prepend">
                        <i class="fa fa-lock"></i>
                        <input type="text" value="" name="" placeholder="密码" class="bottom-radius">
                    </div>

                    <input class="btn btn-success reg-btn" type="button" value="注册">
                    <p class="sign-up-msg">点击 “注册” 即表示您同意并愿意遵守简书<br>
                        用户协议 和 隐私政策 。</p>
                </form>
                <div class="more-sign">
                    <p>社交账号直接注册</p>
                    <ul>
                        <li class="weixin">
                            <a href="#">
                                <i class="fa fa-weixin"></i>
                            </a>
                        </li>
                        <li class="qq">
                            <a href="#">
                                <i class="fa fa-qq"></i>
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
    export default {
        layout:'sign-out',//指明当前页面所使用的默认模板是layouts下的sign.vue
        head(){
            return{
                title:'注册-简书',
                meta:[
                    {hide:'description',name:'description',content:'注册页面'}
                ]
            }

        }
    }
</script>

<style scoped>

</style>