<!--<template>-->
    <!--<div class="basic">-->
        <!--<form>-->
            <!--<div class="avatar" style="display: flex">-->
                <!--<img src="../assets/img/default-avatar.jpg" alt="">-->
                <!--<a class="btn btn-change">-->
                    <!--<input type="file">-->
                    <!--更换头像-->
                <!--</a>-->
            <!--</div>-->
            <!--<div class="formList">-->
                <!--<span>昵称：</span>-->
                <!--<input type="text" value="测试用户">-->
            <!--</div>-->
            <!--<div class="formList">-->
                <!--<span>昵称：</span>-->
                <!--<input type="text" value="测试用户">-->
                <!--<a class="btn btn-change">-->
                    <!--发送-->
                <!--</a>-->
            <!--</div>-->
            <!--<div class="formList">-->
                <!--<span>手机：</span>-->
                <!--<a class="btn btn-change">-->
                    <!--绑定手机-->
                <!--</a>-->
            <!--</div>-->
            <!--<div class="formList">-->
                <!--<span>昵称：</span>-->

            <!--</div>-->
            <!--<div class="formList">-->
                <!--<span>昵称：</span>-->

            <!--</div>-->
            <!--<a class="btn btn-change">-->
                <!--保存-->
            <!--</a>-->


        <!--</form>-->
    <!--</div>-->
<!--</template>-->

<!--<script>-->
  <!--export default {-->
    <!--name: 'settbasic'-->
  <!--}-->
<!--</script>-->

<!--<style scoped>-->
<!--.basic .avatar{-->
    <!--width: 100px;-->
    <!--height: 100px;-->
<!--}-->
<!--.basic .btn-change{-->
    <!--position: relative;-->
    <!--border: 1px solid #42c02e;-->
    <!--width: 90px;-->
    <!--height: 34px;-->
    <!--padding: 4px 12px;-->
    <!--color: #42c02e!important;-->
    <!--border-radius: 20px;-->
    <!--margin-top: 35px;-->
    <!--margin-left: 25px;-->
<!--}-->
<!--.basic .avatar .btn-change>input{-->
    <!--position: absolute;-->
    <!--display: block!important;-->
    <!--width: 82px;-->
    <!--opacity: 0;-->
<!--}-->
<!--.basic .formList{-->
    <!--width: 100%;-->
    <!--padding: 10px;-->
    <!--height: 80px;-->
    <!--line-height: 60px;-->
    <!--/*border: 1px solid red;*/-->
    <!--border-bottom: 1px solid #969696;-->
<!--}-->
<!--.basic .formList input{-->
    <!--width: 60%;-->
    <!--height: 30px;-->
<!--}-->
<!--.basic .formList span{-->
    <!--margin-right: 10%;-->
<!--}-->
<!--.basic .formList a{-->
    <!--margin: 0;-->
    <!--padding: 3px;-->
<!--}-->
<!--</style>-->
<template>
    <div class="basic">
        <form>
            <div class="avatar" style="display: flex">
                <img src="../assets/img/default-avatar.jpg" alt="">
                <a class="btn btn-change">
                    <input type="file">
                    更换头像
                </a>
            </div>
            <div class="formList">
                <span>昵称</span>
                <input type="text" placeholder="测试用户">
            </div>
            <div class="formList">
                <span>电子邮件</span>
                <input type="text" placeholder="请输入你常用邮箱">
                <a class="btn btn-change" style="margin-left: 200px">
                    发送
                </a>
            </div>
            <div class="formList">
                <span>手机</span>
                <a class="btn btn-change">
                    绑定手机
                </a>
            </div>
            <div class="formList bianji">
                <span>常用编辑器</span>
                <input type="radio" id="one"  value="One" v-model="picked">
                <label for="one">富文本</label>
                <input type="radio" id="two"  value="Two" v-model="picked">
                <label for="two">MarkDown</label>

            </div>
            <div class="formList bianji">
                <span>语言设置</span>
                <input type="radio" id="one"  value="One" v-model="language">
                <label for="one">中文简体</label>
                <input type="radio" id="two"  value="Two" v-model="language">
                <label for="two">中文繁体</label>
            </div>
            <div class="formList bianji">
                <span>接收谁的简信</span>
                <input type="radio" id="one"  value="One" v-model="received">
                <label for="one">所有人</label>
                <input type="radio" id="two"  value="Two" v-model="received">
                <label for="two">我关注的人</label>
            </div>
            <div class="formList bianji">
                <span>提醒邮件通知</span>
                <input type="radio" id="one"  value="One" v-model="notice">
                <label for="one">所有动态</label>
                <input type="radio" id="two"  value="Two" v-model="notice">
                <label for="two">每天未读</label>
                <input type="radio" id="three"  value="Three" v-model="notice">
                <label for="three">不接收</label>
            </div>
            <a class="btn btn-change">
                保存
            </a>


        </form>
    </div>
</template>

<script>
  export default {
    name: 'settbasic',
    data(){
      return {
        picked:'',
        language:'',
        received:'',
        notice:''
      }
    }
  }
</script>

<style scoped>
    .basic .avatar{
        width: 100px;
        height: 100px;
    }
    .basic .btn-change{
        position: relative;
        border: 1px solid #42c02e;
        width: 90px;
        height: 34px;
        padding: 4px 12px;
        color: #42c02e!important;
        border-radius: 20px;
        margin-top: 35px;
        margin-left: 25px;
    }
    .basic .avatar .btn-change>input{
        position: absolute;
        display: block!important;
        width: 82px;
        opacity: 0;
    }
    .basic .formList{
        width: 100%;
        padding: 10px;
        height: 80px;
        line-height: 60px;
        border-bottom: 1px solid #f0f0f0;
    }
    .basic .formList input{
        font-size: 12px;
        height:30px;
        border-radius:4px;
        border:1px solid #c8cccf;
        color:#6a6f77;
    }
    .basic .formList span{
        margin-right: 10%;
        color: #969696;
    }
    .basic .formList a{
        margin: 0;
        padding: 3px;
    }
    .basic .bianji input{
        vertical-align: middle;
        margin-right: 10px;
        margin-left: 20px;
    }
</style>
