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
                <span>昵称：</span>
                <input type="text" value="测试用户">
            </div>
            <div class="formList">
                <span>昵称：</span>
                <input type="text" value="测试用户">
                <a class="btn btn-change">
                    发送
                </a>
            </div>
            <div class="formList">
                <span>手机：</span>
                <a class="btn btn-change">
                    绑定手机
                </a>
            </div>
            <div class="formList">
                <span>昵称：</span>

            </div>
            <div class="formList">
                <span>昵称：</span>

            </div>
            <a class="btn btn-change">
                保存
            </a>


        </form>
    </div>
</template>

<script>
  export default {
    name: 'settbasic'
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
    /*border: 1px solid red;*/
    border-bottom: 1px solid #969696;
}
.basic .formList input{
    width: 60%;
    height: 30px;
}
.basic .formList span{
    margin-right: 10%;
}
.basic .formList a{
    margin: 0;
    padding: 3px;
}
</style>