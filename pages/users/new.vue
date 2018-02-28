<template>
    <div>
        <my-header></my-header>
        <div class="my-container" style="padding:50px 0">
            <div class="new-collections">
                <h3>新建专题</h3>
                <table>
                    <tbody class="base">
                    <tr>
                        <td>
                            <div class="avatar-collection">
                                <img src="../../assets/img/default-avatar.jpg">
                            </div>
                        </td>
                        <td>
                            <a class="btn btn-hollow"><input unselectable="on"
                                                             type="file" class="hide">
                            上传专题封面
                            </a>
                        </td>
                    </tr>
                    <tr>
                        <td class="setting-title">名称</td>
                        <td><input type="text" name="nick-name" placeholder="填写名称，不超过50字" class="input"></td>
                    </tr>
                    <tr>
                        <td class="setting-title pull-left setting-input">描述</td>
                        <td><textarea placeholder="填写描述"></textarea></td>
                    </tr>
                    <tr class="add-manager">
                        <td class="setting-title pull-left setting-input">其他管理员</td>
                        <td>
                            <div class="user-add">
                                <input type="text" name="nick-name" placeholder="输入用户名"
                                                         data-toggle="dropdown"  class="input">
                                <ul class="dropdown-menu"></ul>
                            </div>
                        </td>
                    </tr>
                    <tr>
                        <td class="setting-title setting-verticle">是否允许投稿</td>
                        <td class="radio">
                            <div class="col-2"><input type="radio" name="push" value="true"><span>允许</span></div>
                            <div class="col-10"><input type="radio" name="push" value="false"><span>不允许</span></div>
                        </td>
                    </tr>
                    <tr>
                        <td class="setting-title setting-verticle">投稿是否需要审核</td>
                        <td class="radio">
                            <div class="col-2"><input type="radio" name="verify" value="true"> <span>需要</span></div>
                            <div class="col-10"><input type="radio" name="verify" value="false"> <span>不需要</span></div>
                        </td>
                    </tr>
                    </tbody>
                </table>
                <div class="btn btn-success create">创建专题</div>
            </div>
        </div>
    </div>
</template>

<script>
    import myHeader from '~/components/myHeader'

    export default {
        components: {
            myHeader,
        }
    }
</script>

<style scoped>
    .new-collections {
        width: 75%;
        margin: 0 auto;
    }

    .new-collections h3 {
        margin: 10px 0 20px;
        font-size: 21px;
        font-weight: 700;
        color: #333;
    }
    .new-collections table {
        width: 100%;
        border-collapse: separate;
        border-spacing: 2px;
        border-color: grey;
    }
    .new-collections td{
        padding: 16px 0;
        font-size: 15px;
        color: ;
    }
    .new-collections .base .avatar-collection {
        width: 100px;
        height: 100px;
        display: block;
        cursor: pointer;
    }
    .new-collections .base .avatar-collection img {
        width: 100%;
        height: 100%;
        border: 1px solid #ddd;
        border-radius: 10%;
    }
    .new-collections .base .btn-hollow {
        font-size: 14px;
        color: #42c02e;
    }
    .new-collections .base .btn-hollow {
        border: 1px solid rgba(59,194,29,.7);
        color: #42c02e!important;
    }
    .btn-hollow {
        padding: 4px 12px;
        font-size: 12px;
        font-weight: 400;
        line-height: normal;
        border-radius: 40px;
        background: none;
    }
    .btn {
        display: inline-block;
        margin-bottom: 0;
        font-weight: 400;
        text-align: center;
        vertical-align: middle;
        -ms-touch-action: manipulation;
        touch-action: manipulation;
        cursor: pointer;
        border: 1px solid transparent;
        white-space: nowrap;
        padding: 6px 12px;
        font-size: 14px;
        line-height: 1.42857;
        border-radius: 15px;
    }
    .btn:hover{
        background: rgba(59,194,29,.2);
    }
    .new-collections .hide {
        position: absolute;
        display: block!important;
        width: 82px;
        opacity: 0;
    }
    .new-collections .base input.input{
        width: 100%;
    }
    .new-collections .base input {

        padding: 10px 15px;
        font-size: 15px;
        border: 1px solid #c8c8c8;
        border-radius: 4px;
        background-color: hsla(0,0%,71%,.1);
    }
    .new-collections .base textarea {
        width: 100%;
        height: 100px;
        margin-bottom: 10px;
        padding: 10px 15px;
        font-size: 15px;
        border: 1px solid #c8c8c8;
        border-radius: 4px;
        background-color: hsla(0,0%,71%,.1);
        display: block;
        resize: none;
        outline-style: none;
    }
    .new-collections .base .setting-title {
        width: 30%;
        font-size: 15px;
        color: #969696;
    }
    .new-collections .base .setting-verticle {
        vertical-align: bottom;
    }
    .new-collections .base .radio{
        display: flex;
    }
    .new-collections .create{
        margin: 20px 0 50px;
        border-radius: 20px;
        padding: 8px 22px;
        font-size: 16px;
        font-weight: 400;
        line-height: normal;
    }
    .btn-success {
        border-radius: 40px;
        color: #fff;
        background-color: #42c02e;
        border-color: #42c02e;
    }
    .new-collections .create:hover{
        background-color: #42c02e;
        opacity: .8;
    }
</style>